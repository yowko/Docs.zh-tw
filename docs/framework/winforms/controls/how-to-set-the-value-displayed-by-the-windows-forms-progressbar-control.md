---
title: "如何：設定 Windows Form ProgressBar 控制項顯示的值 | Microsoft Docs"
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
  - "Increment 方法"
  - "PerformStep 方法"
  - "進度控制項, 設定顯示的值"
  - "ProgressBar 控制項 [Windows Form], 設定顯示的值"
  - "Step 屬性"
  - "Value 屬性"
ms.assetid: 0e5010ad-1e9a-4271-895e-5a3d24d37a26
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 如何：設定 Windows Form ProgressBar 控制項顯示的值
> [!IMPORTANT]
>  <xref:System.Windows.Forms.ToolStripProgressBar> 控制項會取代 <xref:System.Windows.Forms.ProgressBar> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.ProgressBar> 控制項，以提供回溯相容性及未來使用。  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 對於在 <xref:System.Windows.Forms.ProgressBar> 控制項內部顯示特定值方面，提供數種不同的方式。  您所選擇的方法，端視手邊的工作或正在解決的問題而定。  下表顯示了您可選擇的形式：  
  
|處理方式|描述|  
|----------|--------|  
|直接設定 <xref:System.Windows.Forms.ProgressBar> 控制項的值。|對於已知道所含測量項目總數的工作，例如從資料來源讀取記錄而言，這個方法就很實用。  此外，如果只需要設定值一次或兩次，這個方法也很容易。  最後，如果需要降低進度列所顯示的值，也請使用這個處理序。|  
|以固定值增加 <xref:System.Windows.Forms.ProgressBar> 顯示。|在最小和最大之間顯示簡單計數時，例如已耗用時間或已知總數中已處理的檔案數，這個方法就很實用。|  
|以變化值增加 <xref:System.Windows.Forms.ProgressBar> 顯示。|需要數次以不同數量變更顯示值時，這個方法就很有用。  稍後會提供範例，說明將一系列檔案寫入磁碟時所耗用的硬碟空間量。|  
  
 由進度列顯示該值最直接的方法就是設定 <xref:System.Windows.Forms.ProgressBar.Value%2A> 屬性。  您可以在設計階段或執行階段執行此作業。  
  
### 若要直接設定 ProgressBar 值  
  
1.  設定 <xref:System.Windows.Forms.ProgressBar> 控制項的 <xref:System.Windows.Forms.ProgressBar.Minimum%2A> 和 <xref:System.Windows.Forms.ProgressBar.Maximum%2A> 的值。  
  
2.  在程式碼中，將控制項的 <xref:System.Windows.Forms.ProgressBar.Value%2A> 屬性設定為介於已建立的最小和最大值之間的整數值。  
  
    > [!NOTE]
    >  如果您在由 <xref:System.Windows.Forms.ProgressBar.Minimum%2A> 和 <xref:System.Windows.Forms.ProgressBar.Maximum%2A> 屬性建立的界限之外，設定 <xref:System.Windows.Forms.ProgressBar.Value%2A> 屬性，此控制項會擲回 <xref:System.ArgumentException> 例外狀況。  
  
     下列程式碼範例說明如何直接設定 <xref:System.Windows.Forms.ProgressBar> 值。  程式碼會從資料來源讀取記錄，然後在每次讀取資料記錄時更新進度列和標籤。  這個範例需要您的表單具有 <xref:System.Windows.Forms.Label> 控制項、<xref:System.Windows.Forms.ProgressBar> 控制項，以及具有稱為 `CustomerRow`  的資料列 \(其中包含 `FirstName`  和 `Last Name`  欄位\) 的資料表。  
  
    ```vb  
    Public Sub CreateNewRecords()  
       ' Sets the progress bar's Maximum property to  
       ' the total number of records to be created.  
       ProgressBar1.Maximum = 20  
  
       ' Creates a new record in the dataset.  
       ' NOTE: The code below will not compile, it merely  
       ' illustrates how the progress bar would be used.  
       Dim anyRow As CustomerRow = DatasetName.ExistingTable.NewRow  
       anyRow.FirstName = "Stephen"  
       anyRow.LastName = "James"  
       ExistingTable.Rows.Add(anyRow)  
  
       ' Increases the value displayed by the progress bar.  
       ProgressBar1.Value += 1  
       ' Updates the label to show that a record was read.  
       Label1.Text = "Records Read = " & ProgressBar1.Value.ToString()  
    End Sub  
  
    ```  
  
    ```csharp  
    public void createNewRecords()  
    {  
       // Sets the progress bar's Maximum property to  
       // the total number of records to be created.  
       progressBar1.Maximum = 20;  
  
       // Creates a new record in the dataset.  
       // NOTE: The code below will not compile, it merely  
       // illustrates how the progress bar would be used.  
       CustomerRow anyRow = DatasetName.ExistingTable.NewRow();  
       anyRow.FirstName = "Stephen";  
       anyRow.LastName = "James";  
       ExistingTable.Rows.Add(anyRow);  
  
       // Increases the value displayed by the progress bar.  
       progressBar1.Value += 1;  
       // Updates the label to show that a record was read.  
       label1.Text = "Records Read = " + progressBar1.Value.ToString();  
    }  
    ```  
  
     如果顯示的進度是以固定間隔進行，則可設定該值，然後呼叫方法，以該間隔增加 <xref:System.Windows.Forms.ProgressBar> 控制項的值。  對於計時器和未以整體百分比測量進度的其他案例而言，這個方法很有用。  
  
### 若要以固定值增加進度列  
  
1.  設定 <xref:System.Windows.Forms.ProgressBar> 控制項的 <xref:System.Windows.Forms.ProgressBar.Minimum%2A> 和 <xref:System.Windows.Forms.ProgressBar.Maximum%2A> 的值。  
  
2.  將控制項的 <xref:System.Windows.Forms.ProgressBar.Step%2A> 屬性設定為整數，表示增加進度列顯示值的數量。  
  
3.  呼叫 <xref:System.Windows.Forms.ProgressBar.PerformStep%2A> 方法，依在 <xref:System.Windows.Forms.ProgressBar.Step%2A> 屬性中設定的數量變更顯示值。  
  
     下列程式碼範例說明進度列如何在複製作業中維持檔案計數。  
  
     在下列範例中，當每個檔案讀取至記憶體時，系統會更新進度列和標籤，以反映讀取的檔案總數。  在這個範例中，您的表單必須有 <xref:System.Windows.Forms.Label> 控制項和 <xref:System.Windows.Forms.ProgressBar> 控制項。  
  
    ```vb  
    Public Sub LoadFiles()  
       ' Sets the progress bar's minimum value to a number representing  
       ' no operations complete -- in this case, no files read.  
       ProgressBar1.Minimum = 0  
       ' Sets the progress bar's maximum value to a number representing  
       ' all operations complete -- in this case, all five files read.  
       ProgressBar1.Maximum = 5  
       ' Sets the Step property to amount to increase with each iteration.  
       ' In this case, it will increase by one with every file read.  
       ProgressBar1.Step = 1  
  
       ' Dimensions a counter variable.  
       Dim i As Integer  
       ' Uses a For...Next loop to iterate through the operations to be  
       ' completed. In this case, five files are to be copied into memory,  
       ' so the loop will execute 5 times.  
       For i = 0 To 4  
          ' Insert code to copy a file  
          ProgressBar1.PerformStep()  
          ' Update the label to show that a file was read.  
          Label1.Text = "# of Files Read = " & ProgressBar1.Value.ToString  
       Next i  
    End Sub  
  
    ```  
  
    ```csharp  
    public void loadFiles()  
    {  
       // Sets the progress bar's minimum value to a number representing  
       // no operations complete -- in this case, no files read.  
       progressBar1.Minimum = 0;  
       // Sets the progress bar's maximum value to a number representing  
       // all operations complete -- in this case, all five files read.  
       progressBar1.Maximum = 5;  
       // Sets the Step property to amount to increase with each iteration.  
       // In this case, it will increase by one with every file read.  
       progressBar1.Step = 1;  
  
       // Uses a for loop to iterate through the operations to be  
       // completed. In this case, five files are to be copied into memory,  
       // so the loop will execute 5 times.  
       for (int i = 0; i <= 4; i++)  
       {  
          // Inserts code to copy a file  
          progressBar1.PerformStep();  
          // Updates the label to show that a file was read.  
          label1.Text = "# of Files Read = " + progressBar1.Value.ToString();  
       }  
    }  
    ```  
  
     最後，您可以增加進度列的顯示值，如此一來每次增加的數量都是唯一的。  在追蹤一系列唯一作業時，例如將不同大小的檔案寫入磁碟，或是以整體百分比測量進度時，這個方法就很有用。  
  
### 若要以動態值增加進度列  
  
1.  設定 <xref:System.Windows.Forms.ProgressBar> 控制項的 <xref:System.Windows.Forms.ProgressBar.Minimum%2A> 和 <xref:System.Windows.Forms.ProgressBar.Maximum%2A> 的值。  
  
2.  呼叫 <xref:System.Windows.Forms.ProgressBar.Increment%2A> 方法，依您指定的整數變更顯示值。  
  
     下列程式碼範例說明進度列如何計算複製作業期間，已經使用的磁碟空間有多少。  
  
     在下列範例中，當每個檔案寫入硬碟時，進度列和標籤會進行更新，以反映可用的硬碟空間量。  在這個範例中，您的表單必須有 <xref:System.Windows.Forms.Label> 控制項和 <xref:System.Windows.Forms.ProgressBar> 控制項。  
  
    ```vb  
    Public Sub ReadFiles()  
       ' Sets the progress bar's minimum value to a number   
       ' representing the hard disk space before the files are read in.  
       ' You will most likely have to set this using a system call.  
       ' NOTE: The code below is meant to be an example and  
       ' will not compile.  
       ProgressBar1.Minimum = AvailableDiskSpace()  
       ' Sets the progress bar's maximum value to a number   
       ' representing the total hard disk space.  
       ' You will most likely have to set this using a system call.  
       ' NOTE: The code below is meant to be an example   
       ' and will not compile.  
       ProgressBar1.Maximum = TotalDiskSpace()  
  
       ' Dimension a counter variable.  
       Dim i As Integer  
       ' Uses a For...Next loop to iterate through the operations to be  
       ' completed. In this case, five files are to be written to the disk,  
       ' so it will execute the loop 5 times.  
       For i = 1 To 5  
          ' Insert code to read a file into memory and update file size.  
          ' Increases the progress bar's value based on the size of   
          ' the file currently being written.  
          ProgressBar1.Increment(FileSize)  
          ' Updates the label to show available drive space.  
          Label1.Text = "Current Disk Space Used = " &_   
          ProgressBar1.Value.ToString()  
       Next i  
    End Sub  
  
    ```  
  
    ```csharp  
    public void readFiles()  
    {  
       // Sets the progress bar's minimum value to a number   
       // representing the hard disk space before the files are read in.  
       // You will most likely have to set this using a system call.  
       // NOTE: The code below is meant to be an example and   
       // will not compile.  
       progressBar1.Minimum = AvailableDiskSpace();  
       // Sets the progress bar's maximum value to a number   
       // representing the total hard disk space.  
       // You will most likely have to set this using a system call.  
       // NOTE: The code below is meant to be an example   
       // and will not compile.  
       progressBar1.Maximum = TotalDiskSpace();  
  
       // Uses a for loop to iterate through the operations to be  
       // completed. In this case, five files are to be written  
       // to the disk, so it will execute the loop 5 times.  
       for (int i = 1; i<= 5; i++)  
       {  
          // Insert code to read a file into memory and update file size.  
          // Increases the progress bar's value based on the size of   
          // the file currently being written.  
          progressBar1.Increment(FileSize);  
          // Updates the label to show available drive space.  
          label1.Text = "Current Disk Space Used = " + progressBar1.Value.ToString();  
       }  
    }  
    ```  
  
## 請參閱  
 <xref:System.Windows.Forms.ProgressBar>   
 <xref:System.Windows.Forms.ToolStripProgressBar>   
 [ProgressBar 控制項概觀](../../../../docs/framework/winforms/controls/progressbar-control-overview-windows-forms.md)   
 [ProgressBar 控制項](../../../../docs/framework/winforms/controls/progressbar-control-windows-forms.md)