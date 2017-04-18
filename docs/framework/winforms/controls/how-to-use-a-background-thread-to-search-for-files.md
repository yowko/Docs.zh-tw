---
title: "如何：使用背景執行緒搜尋檔案 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "自訂控制項 [Windows Form], 多執行緒"
  - "自訂控制項 [Windows Form], 範例"
  - "多執行緒 Windows Form 控制項範例 [Windows Form]"
  - "執行緒處理 [Windows Form], 自訂控制項"
ms.assetid: 7fe3956f-5b8f-4f78-8aae-c9eb0b28f13a
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 如何：使用背景執行緒搜尋檔案
<xref:System.ComponentModel.BackgroundWorker> 元件會取代並加入功能至 <xref:System.Threading> 命名空間；不過，您可以依選擇為回溯相容性 \(Backward Compatibility\) 和未來使用而保留 <xref:System.Threading> 命名空間。  如需詳細資訊，請參閱 [BackgroundWorker 元件概觀](../../../../docs/framework/winforms/controls/backgroundworker-component-overview.md)。  
  
 Windows Form 使用單一執行緒 Apartment Model \(STA\)，因為 Windows Form 的架構是以本質上即是 Apartment 執行緒的原生 Win32 Windows 為基礎。  STA 模型表示可以在任何執行緒上建立視窗，但建立後則不可以在執行緒間切換，且所有呼叫它的函式必須存在於它的建立執行緒上。  除了 Windows Form 以外，.NET Framework 中的類別是使用無限制執行緒模型 \(Free Threading Model\)。  如需 .NET Framework 中執行緒的詳細資訊，請參閱 [Threading](../../../../docs/standard/threading/index.md)。  
  
 STA 模型對需在控制項的建立執行緒之外呼叫的控制項，會要求該控制項的任何方法必須封送 \(Marshal\) 給 \(執行於\) 控制項的建立執行緒處理。  基底類別 <xref:System.Windows.Forms.Control> 類別提供幾個方法 \(<xref:System.Windows.Forms.Control.Invoke%2A>、<xref:System.Windows.Forms.Control.BeginInvoke%2A> 和 <xref:System.Windows.Forms.Control.EndInvoke%2A>\) 來達成此目的。  <xref:System.Windows.Forms.Control.Invoke%2A> 會產生同步方法呼叫；<xref:System.Windows.Forms.Control.BeginInvoke%2A> 則會產生非同步方法呼叫。  
  
 當您在控制項中使用多執行緒來處理耗用資源的工作時，因為耗用資源的作業是在背景 \(Background\) 執行緒上執行，所以使用者介面仍然可以正常回應。  
  
 下列範例 \(`DirectorySearcher`\) 將說明一個使用背景執行緒的多執行緒 Windows Form 控制項，它將以指定的搜尋字串遞迴搜尋目錄中相符的檔案，然後將搜尋結果填入 \(Populate\) 清單方塊。  以下為範例中所描述的重要概念。  
  
-   `DirectorySearcher` 將啟動一個新執行緒以執行搜尋作業。  之後執行 `ThreadProcedure` 方法的執行緒會呼叫 Helper `RecurseDirectory` 方法以執行實際的搜尋和填入清單方塊作業。  但是，填入清單方塊作業需要執行的跨執行緒 \(Cross\-Thread\) 呼叫將在稍後的項目符號中說明。  
  
-   `DirectorySearcher` 會定義將檔案加入至清單方塊的 `AddFiles` 方法；而 `RecurseDirectory` 則不可以直接叫用 `AddFiles`，因為 `AddFiles` 只可在建立 `DirectorySearcher` 的 STA 執行緒中執行。  
  
-   `RecurseDirectory` 只能透過跨執行緒呼叫的方式呼叫 `AddFiles`，也就是必須呼叫 <xref:System.Windows.Forms.Control.Invoke%2A> 或 <xref:System.Windows.Forms.Control.BeginInvoke%2A> 而將 `AddFiles` 封送至 `DirectorySearcher` 的建立執行緒。  `RecurseDirectory` 使用 <xref:System.Windows.Forms.Control.BeginInvoke%2A> 以執行非同步呼叫。  
  
-   將方法封送處理需要使用函式指標或回呼 \(Callback\)。  在 .NET Framework 中使用委派即可達成此目的。  <xref:System.Windows.Forms.Control.BeginInvoke%2A> 會將委派視為引數。  `DirectorySearcher` 即可定義一個委派 \(`FileListDelegate`\)、在它的建構函式中將 `AddFiles` 繫結於 `FileListDelegate` 的執行個體，然後將這個委派執行個體傳遞給 <xref:System.Windows.Forms.Control.BeginInvoke%2A>。  `DirectorySearcher` 同時也會定義在完成搜尋後要封送處理的事件委派。  
  
```vb  
Option Strict  
Option Explicit  
  
Imports System  
Imports System.IO  
Imports System.Threading  
Imports System.Windows.Forms  
  
Namespace Microsoft.Samples.DirectorySearcher  
   ' <summary>  
   '      This class is a Windows Forms control that implements a simple directory searcher.  
   '      You provide, through code, a search string and it will search directories on  
   '      a background thread, populating its list box with matches.  
   ' </summary>  
   Public Class DirectorySearcher  
      Inherits Control  
      ' Define a special delegate that handles marshaling  
      ' lists of file names from the background directory search  
      ' thread to the thread that contains the list box.  
      Delegate Sub FileListDelegate(files() As String, startIndex As Integer, count As Integer)  
  
      Private _listBox As ListBox  
      Private _searchCriteria As String  
      Private _searching As Boolean  
      Private _deferSearch As Boolean  
      Private _searchThread As Thread  
      Private _fileListDelegate As FileListDelegate  
      Private _onSearchComplete As EventHandler  
  
      Public Sub New()  
         _listBox = New ListBox()  
         _listBox.Dock = DockStyle.Fill  
  
         Controls.Add(_listBox)  
  
         _fileListDelegate = New FileListDelegate(AddressOf AddFiles)  
         _onSearchComplete = New EventHandler(AddressOf OnSearchComplete)  
      End Sub  
  
      Public Property SearchCriteria() As String  
         Get  
            Return _searchCriteria  
         End Get  
         Set  
            ' If currently searching, abort  
            ' the search and restart it after  
            ' setting the new criteria.  
            '  
            Dim wasSearching As Boolean = Searching  
  
            If wasSearching Then  
               StopSearch()  
            End If  
  
            _listBox.Items.Clear()  
            _searchCriteria = value  
  
            If wasSearching Then  
               BeginSearch()  
            End If  
         End Set  
      End Property  
  
      Public ReadOnly Property Searching() As Boolean  
         Get  
            Return _searching  
         End Get  
      End Property  
  
      Public Event SearchComplete As EventHandler  
  
      ' <summary>  
      ' This method is called from the background thread.  It is called through  
      ' a BeginInvoke call so that it is always marshaled to the thread that  
      ' owns the list box control.  
      ' </summary>  
      ' <param name="files"></param>  
      ' <param name="startIndex"></param>  
      ' <param name="count"></param>  
      Private Sub AddFiles(files() As String, startIndex As Integer, count As Integer)  
         While count > 0  
            count -= 1  
            _listBox.Items.Add(files((startIndex + count)))  
         End While  
      End Sub  
  
      Public Sub BeginSearch()  
         ' Create the search thread, which   
         ' will begin the search.  
         ' If already searching, do nothing.  
         '  
         If Searching Then  
            Return  
         End If  
  
         ' Start the search if the handle has  
         ' been created. Otherwise, defer it until the  
         ' handle has been created.  
         If IsHandleCreated Then  
            _searchThread = New Thread(New ThreadStart(AddressOf ThreadProcedure))  
            _searching = True  
            _searchThread.Start()  
         Else  
            _deferSearch = True  
         End If  
      End Sub  
  
      Protected Overrides Sub OnHandleDestroyed(e As EventArgs)  
         ' If the handle is being destroyed and you are not  
         ' recreating it, then abort the search.  
         If Not RecreatingHandle Then  
            StopSearch()  
         End If  
         MyBase.OnHandleDestroyed(e)  
      End Sub  
  
      Protected Overrides Sub OnHandleCreated(e As EventArgs)  
         MyBase.OnHandleCreated(e)  
         If _deferSearch Then  
            _deferSearch = False  
            BeginSearch()  
         End If  
      End Sub  
  
      ' <summary>  
      ' This method is called by the background thread when it has  
      ' finished the search.  
      ' </summary>  
      ' <param name="sender"></param>  
      ' <param name="e"></param>  
      Private Sub OnSearchComplete(sender As Object, e As EventArgs)  
         RaiseEvent SearchComplete(sender, e)  
      End Sub  
  
      Public Sub StopSearch()  
         If Not _searching Then  
            Return  
         End If  
  
         If _searchThread.IsAlive Then  
            _searchThread.Abort()  
            _searchThread.Join()  
         End If  
  
         _searchThread = Nothing  
         _searching = False  
      End Sub  
  
      ' <summary>  
      ' Recurses the given path, adding all files on that path to   
      ' the list box. After it finishes with the files, it  
      ' calls itself once for each directory on the path.  
      ' </summary>  
      ' <param name="searchPath"></param>  
      Private Sub RecurseDirectory(searchPath As String)  
         ' Split searchPath into a directory and a wildcard specification.  
         '  
         Dim directoryPath As String = Path.GetDirectoryName(searchPath)  
         Dim search As String = Path.GetFileName(searchPath)  
  
         ' If a directory or search criteria are not specified, then return.  
         '  
         If directoryPath Is Nothing Or search Is Nothing Then  
            Return  
         End If  
  
         Dim files() As String  
  
         ' File systems like NTFS that have  
         ' access permissions might result in exceptions  
         ' when looking into directories without permission.  
         ' Catch those exceptions and return.  
         Try  
            files = Directory.GetFiles(directoryPath, search)  
         Catch e As UnauthorizedAccessException  
            Return  
         Catch e As DirectoryNotFoundException  
            Return  
         End Try  
  
         ' Perform a BeginInvoke call to the list box  
         ' in order to marshal to the correct thread. It is not  
         ' very efficient to perform this marshal once for every  
         ' file, so batch up multiple file calls into one  
         ' marshal invocation.  
         Dim startingIndex As Integer = 0  
         While startingIndex < files.Length  
            ' Batch up 20 files at once, unless at the  
            ' end.  
            '  
            Dim count As Integer = 20  
            If count + startingIndex >= files.Length Then  
               count = files.Length - startingIndex  
            End If  
            ' Begin the cross-thread call. Because you are passing  
            ' immutable objects into this invoke method, you do not have to  
            ' wait for it to finish. If these were complex objects, you would  
            ' have to either create new instances of them or   
            ' wait for the thread to process this invoke before modifying  
            ' the objects.  
            Dim r As IAsyncResult = BeginInvoke(_fileListDelegate, New Object() {files, startingIndex, count})  
            startingIndex += count  
         End While  
         ' Now that you have finished the files in this directory, recurse  
         ' for each subdirectory.  
         Dim directories As String() = Directory.GetDirectories(directoryPath)  
         Dim d As String  
         For Each d In  directories  
            RecurseDirectory(Path.Combine(d, search))  
         Next d  
      End Sub  
  
      '/ <summary>  
      '/ This is the actual thread procedure. This method runs in a background  
      '/ thread to scan directories. When finished, it simply exits.  
      '/ </summary>  
      Private Sub ThreadProcedure()  
         ' Get the search string. Individual   
         ' field assigns are atomic in .NET, so you do not  
         ' need to use any thread synchronization to grab  
         ' the string value here.  
         Try  
            Dim localSearch As String = SearchCriteria  
  
            ' Now, search the file system.  
            '  
            RecurseDirectory(localSearch)  
         Finally  
            ' You are done with the search, so update.  
            '  
            _searching = False  
  
            ' Raise an event that notifies the user that  
            ' the search has terminated.    
            ' You do not have to do this through a marshaled call, but  
            ' marshaling is recommended for the following reason:  
            ' Users of this control do not know that it is  
            ' multithreaded, so they expect its events to   
            ' come back on the same thread as the control.  
            BeginInvoke(_onSearchComplete, New Object() {Me, EventArgs.Empty})  
         End Try  
      End Sub  
   End Class  
End Namespace  
  
```  
  
```csharp  
namespace Microsoft.Samples.DirectorySearcher  
{  
   using System;  
   using System.IO;  
   using System.Threading;  
   using System.Windows.Forms;  
  
   /// <summary>  
   ///      This class is a Windows Forms control that implements a simple directory searcher.  
   ///      You provide, through code, a search string and it will search directories on  
   ///      a background thread, populating its list box with matches.  
   /// </summary>  
   public class DirectorySearcher : Control  
   {  
      // Define a special delegate that handles marshaling  
      // lists of file names from the background directory search  
      // thread to the thread that contains the list box.  
      private delegate void FileListDelegate(string[] files, int startIndex, int count);  
  
      private ListBox listBox;  
      private string  searchCriteria;  
      private bool searching;  
      private bool deferSearch;  
      private Thread searchThread;  
      private FileListDelegate fileListDelegate;  
      private EventHandler onSearchComplete;  
  
      public DirectorySearcher()  
      {  
         listBox = new ListBox();  
         listBox.Dock = DockStyle.Fill;  
  
         Controls.Add(listBox);  
  
         fileListDelegate = new FileListDelegate(AddFiles);  
         onSearchComplete = new EventHandler(OnSearchComplete);  
      }  
  
      public string SearchCriteria   
      {  
         get   
         {  
            return searchCriteria;  
         }  
         set   
         {  
            // If currently searching, abort  
            // the search and restart it after  
            // setting the new criteria.  
            //  
            bool wasSearching = Searching;  
  
            if (wasSearching)  
            {  
               StopSearch();  
            }  
  
            listBox.Items.Clear();  
            searchCriteria = value;  
  
            if (wasSearching)  
            {  
               BeginSearch();  
            }  
         }  
      }  
  
      public bool Searching   
      {  
         get   
         {  
            return searching;  
         }  
      }  
  
      public event EventHandler SearchComplete;  
  
      /// <summary>  
      /// This method is called from the background thread. It is called through  
      /// a BeginInvoke call so that it is always marshaled to the thread that  
      /// owns the list box control.  
      /// </summary>  
      /// <param name="files"></param>  
      /// <param name="startIndex"></param>  
      /// <param name="count"></param>  
      private void AddFiles(string[] files, int startIndex, int count)  
      {  
         while(count-- > 0)  
         {  
            listBox.Items.Add(files[startIndex + count]);  
         }  
      }  
  
      public void BeginSearch()   
      {  
         // Create the search thread, which   
         // will begin the search.  
         // If already searching, do nothing.  
         //  
         if (Searching)  
         {  
            return;  
         }  
  
         // Start the search if the handle has  
         // been created. Otherwise, defer it until the  
         // handle has been created.  
         if (IsHandleCreated)  
         {  
            searchThread = new Thread(new ThreadStart(ThreadProcedure));  
            searching = true;  
            searchThread.Start();  
         }  
         else  
         {  
            deferSearch = true;  
         }  
      }  
  
      protected override void OnHandleDestroyed(EventArgs e)  
      {  
         // If the handle is being destroyed and you are not  
         // recreating it, then abort the search.  
         if (!RecreatingHandle)  
         {  
            StopSearch();  
         }  
         base.OnHandleDestroyed(e);  
      }  
  
      protected override void OnHandleCreated(EventArgs e)   
      {  
         base.OnHandleCreated(e);  
         if (deferSearch)  
         {  
            deferSearch = false;  
            BeginSearch();  
         }  
      }  
  
      /// <summary>  
      /// This method is called by the background thread when it has finished  
      /// the search.  
      /// </summary>  
      /// <param name="sender"></param>  
      /// <param name="e"></param>  
      private void OnSearchComplete(object sender, EventArgs e)  
      {  
         if (SearchComplete != null)  
         {  
            SearchComplete(sender, e);  
         }  
      }  
  
      public void StopSearch()  
      {  
         if (!searching)  
         {  
            return;  
         }  
  
         if (searchThread.IsAlive)  
         {  
            searchThread.Abort();  
            searchThread.Join();  
         }  
  
         searchThread = null;  
         searching = false;  
      }  
  
      /// <summary>  
      /// Recurses the given path, adding all files on that path to   
      /// the list box. After it finishes with the files, it  
      /// calls itself once for each directory on the path.  
      /// </summary>  
      /// <param name="searchPath"></param>  
      private void RecurseDirectory(string searchPath)  
      {  
         // Split searchPath into a directory and a wildcard specification.  
         //  
         string directory = Path.GetDirectoryName(searchPath);  
         string search = Path.GetFileName(searchPath);  
  
         // If a directory or search criteria are not specified, then return.  
         //  
         if (directory == null || search == null)  
         {  
            return;  
         }  
  
         string[] files;  
  
         // File systems like NTFS that have  
         // access permissions might result in exceptions  
         // when looking into directories without permission.  
         // Catch those exceptions and return.  
         try   
         {  
            files = Directory.GetFiles(directory, search);  
         }  
         catch(UnauthorizedAccessException)  
         {  
            return;  
         }  
         catch(DirectoryNotFoundException)  
         {  
            return;  
         }  
  
         // Perform a BeginInvoke call to the list box  
         // in order to marshal to the correct thread. It is not  
         // very efficient to perform this marshal once for every  
         // file, so batch up multiple file calls into one  
         // marshal invocation.  
         int startingIndex = 0;  
  
         while(startingIndex < files.Length)  
         {  
            // Batch up 20 files at once, unless at the  
            // end.  
            //  
            int count = 20;  
            if (count + startingIndex >= files.Length)  
            {  
               count = files.Length - startingIndex;  
            }  
  
            // Begin the cross-thread call. Because you are passing  
            // immutable objects into this invoke method, you do not have to  
            // wait for it to finish. If these were complex objects, you would  
            // have to either create new instances of them or   
            // wait for the thread to process this invoke before modifying  
            // the objects.  
            IAsyncResult r = BeginInvoke(fileListDelegate, new object[] {files, startingIndex, count});  
            startingIndex += count;  
         }  
  
         // Now that you have finished the files in this directory, recurse for  
         // each subdirectory.  
         string[] directories = Directory.GetDirectories(directory);  
         foreach(string d in directories)  
         {  
            RecurseDirectory(Path.Combine(d, search));  
         }  
      }  
  
      /// <summary>  
      /// This is the actual thread procedure. This method runs in a background  
      /// thread to scan directories. When finished, it simply exits.  
      /// </summary>  
      private void ThreadProcedure()  
      {  
         // Get the search string. Individual   
         // field assigns are atomic in .NET, so you do not  
         // need to use any thread synchronization to grab  
         // the string value here.  
         try   
         {  
            string localSearch = SearchCriteria;  
  
            // Now, search the file system.  
            //  
            RecurseDirectory(localSearch);  
         }  
         finally  
         {  
            // You are done with the search, so update.  
            //  
            searching = false;  
  
            // Raise an event that notifies the user that  
            // the search has terminated.    
            // You do not have to do this through a marshaled call, but  
            // marshaling is recommended for the following reason:  
            // Users of this control do not know that it is  
            // multithreaded, so they expect its events to   
            // come back on the same thread as the control.  
            BeginInvoke(onSearchComplete, new object[] {this, EventArgs.Empty});  
         }  
      }  
   }  
}  
```  
  
## 在表單上使用多執行緒控制項  
 下列範例將說明如何在表單上使用多執行緒 `DirectorySearcher` 控制項。  
  
```vb  
Option Explicit  
Option Strict  
  
Imports Microsoft.Samples.DirectorySearcher  
Imports System  
Imports System.Drawing  
Imports System.Collections  
Imports System.ComponentModel  
Imports System.Windows.Forms  
Imports System.Data  
  
Namespace SampleUsage  
  
   ' <summary>  
   '      Summary description for Form1.  
   ' </summary>  
   Public Class Form1  
      Inherits System.Windows.Forms.Form  
      Private WithEvents directorySearcher As DirectorySearcher  
      Private searchText As System.Windows.Forms.TextBox  
      Private searchLabel As System.Windows.Forms.Label  
      Private WithEvents searchButton As System.Windows.Forms.Button  
  
      Public Sub New()  
         '  
         ' Required for Windows Forms designer support.  
         '  
         InitializeComponent()  
         '  
         ' Add any constructor code after InitializeComponent call here.  
         '  
      End Sub  
  
      #Region "Windows Form Designer generated code"  
      ' <summary>  
      '      Required method for designer support. Do not modify  
      '      the contents of this method with the code editor.  
      ' </summary>  
      Private Sub InitializeComponent()  
         Me.directorySearcher = New Microsoft.Samples.DirectorySearcher.DirectorySearcher()  
         Me.searchButton = New System.Windows.Forms.Button()  
         Me.searchText = New System.Windows.Forms.TextBox()  
         Me.searchLabel = New System.Windows.Forms.Label()  
         Me.directorySearcher.Anchor = System.Windows.Forms.AnchorStyles.Top Or System.Windows.Forms.AnchorStyles.Bottom Or System.Windows.Forms.AnchorStyles.Left Or System.Windows.Forms.AnchorStyles.Right  
         Me.directorySearcher.Location = New System.Drawing.Point(8, 72)  
         Me.directorySearcher.SearchCriteria = Nothing  
         Me.directorySearcher.Size = New System.Drawing.Size(271, 173)  
         Me.directorySearcher.TabIndex = 2  
         Me.searchButton.Location = New System.Drawing.Point(8, 16)  
         Me.searchButton.Size = New System.Drawing.Size(88, 40)  
         Me.searchButton.TabIndex = 0  
         Me.searchButton.Text = "&Search"  
         Me.searchText.Anchor = System.Windows.Forms.AnchorStyles.Top Or System.Windows.Forms.AnchorStyles.Left Or System.Windows.Forms.AnchorStyles.Right  
         Me.searchText.Location = New System.Drawing.Point(104, 24)  
         Me.searchText.Size = New System.Drawing.Size(175, 20)  
         Me.searchText.TabIndex = 1  
         Me.searchText.Text = "c:\*.cs"  
         Me.searchLabel.ForeColor = System.Drawing.Color.Red  
         Me.searchLabel.Location = New System.Drawing.Point(104, 48)  
         Me.searchLabel.Size = New System.Drawing.Size(176, 16)  
         Me.searchLabel.TabIndex = 3  
         Me.ClientSize = New System.Drawing.Size(291, 264)  
         Me.Controls.AddRange(New System.Windows.Forms.Control() {Me.searchLabel, Me.directorySearcher, Me.searchText, Me.searchButton})  
         Me.Text = "Search Directories"  
      End Sub  
      #End Region  
  
      ' <summary>  
      '    The main entry point for the application.  
      ' </summary>  
      <STAThread()> _  
      Shared Sub Main()  
         Application.Run(New Form1())  
      End Sub  
  
      Private Sub searchButton_Click(sender As Object, e As System.EventArgs) Handles searchButton.Click  
         directorySearcher.SearchCriteria = searchText.Text  
         searchLabel.Text = "Searching..."  
         directorySearcher.BeginSearch()  
      End Sub  
  
      Private Sub directorySearcher_SearchComplete(sender As Object, e As System.EventArgs) Handles directorySearcher.SearchComplete  
         searchLabel.Text = String.Empty  
      End Sub  
   End Class  
End Namespace  
  
```  
  
```csharp  
namespace SampleUsage  
{  
   using Microsoft.Samples.DirectorySearcher;  
   using System;  
   using System.Drawing;  
   using System.Collections;  
   using System.ComponentModel;  
   using System.Windows.Forms;  
   using System.Data;  
  
   /// <summary>  
   ///      Summary description for Form1.  
   /// </summary>  
   public class Form1 : System.Windows.Forms.Form  
   {  
      private DirectorySearcher directorySearcher;  
      private System.Windows.Forms.TextBox searchText;  
      private System.Windows.Forms.Label searchLabel;  
      private System.Windows.Forms.Button searchButton;  
  
      public Form1()  
      {  
         //  
         // Required for Windows Forms designer support.  
         //  
         InitializeComponent();  
  
         //  
         // Add any constructor code after InitializeComponent call here.  
         //  
      }  
  
      #region Windows Form Designer generated code  
      /// <summary>  
      ///      Required method for designer support. Do not modify  
      ///      the contents of this method with the code editor.  
      /// </summary>  
      private void InitializeComponent()  
      {  
         this.directorySearcher = new Microsoft.Samples.DirectorySearcher.DirectorySearcher();  
         this.searchButton = new System.Windows.Forms.Button();  
         this.searchText = new System.Windows.Forms.TextBox();  
         this.searchLabel = new System.Windows.Forms.Label();  
         this.directorySearcher.Anchor = (((System.Windows.Forms.AnchorStyles.Top | System.Windows.Forms.AnchorStyles.Bottom)   
            | System.Windows.Forms.AnchorStyles.Left)   
            | System.Windows.Forms.AnchorStyles.Right);  
         this.directorySearcher.Location = new System.Drawing.Point(8, 72);  
         this.directorySearcher.SearchCriteria = null;  
         this.directorySearcher.Size = new System.Drawing.Size(271, 173);  
         this.directorySearcher.TabIndex = 2;  
         this.directorySearcher.SearchComplete += new System.EventHandler(this.directorySearcher_SearchComplete);  
         this.searchButton.Location = new System.Drawing.Point(8, 16);  
         this.searchButton.Size = new System.Drawing.Size(88, 40);  
         this.searchButton.TabIndex = 0;  
         this.searchButton.Text = "&Search";  
         this.searchButton.Click += new System.EventHandler(this.searchButton_Click);  
         this.searchText.Anchor = ((System.Windows.Forms.AnchorStyles.Top | System.Windows.Forms.AnchorStyles.Left)   
            | System.Windows.Forms.AnchorStyles.Right);  
         this.searchText.Location = new System.Drawing.Point(104, 24);  
         this.searchText.Size = new System.Drawing.Size(175, 20);  
         this.searchText.TabIndex = 1;  
         this.searchText.Text = "c:\\*.cs";  
         this.searchLabel.ForeColor = System.Drawing.Color.Red;  
         this.searchLabel.Location = new System.Drawing.Point(104, 48);  
         this.searchLabel.Size = new System.Drawing.Size(176, 16);  
         this.searchLabel.TabIndex = 3;  
         this.ClientSize = new System.Drawing.Size(291, 264);  
         this.Controls.AddRange(new System.Windows.Forms.Control[] {this.searchLabel,  
                                                        this.directorySearcher,  
                                                        this.searchText,  
                                                        this.searchButton});  
         this.Text = "Search Directories";  
  
      }  
      #endregion  
  
      /// <summary>  
      ///    The main entry point for the application.  
      /// </summary>  
      [STAThread]  
      static void Main()   
      {  
         Application.Run(new Form1());  
      }  
  
      private void searchButton_Click(object sender, System.EventArgs e)  
      {  
         directorySearcher.SearchCriteria = searchText.Text;  
         searchLabel.Text = "Searching...";  
         directorySearcher.BeginSearch();  
      }  
  
      private void directorySearcher_SearchComplete(object sender, System.EventArgs e)  
      {  
         searchLabel.Text = string.Empty;  
      }  
   }  
}  
```  
  
## 請參閱  
 <xref:System.ComponentModel.BackgroundWorker>   
 [使用 .NET Framework 開發自訂的 Windows Form 控制項](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)   
 [Event\-based Asynchronous Pattern Overview](../../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)