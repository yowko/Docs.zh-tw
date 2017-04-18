---
title: "逐步解說：在設計階段偵錯自訂的 Windows Form 控制項 | Microsoft Docs"
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
  - "控制項 [Windows Form], 偵錯"
  - "自訂控制項 [Windows Form], 偵錯"
  - "自訂控制項 [Windows Form], 逐步解說"
  - "偵錯 [Visual Studio], 逐步解說"
  - "偵錯 [Visual Studio], Windows Form"
  - "設計工具"
  - "設計階段偵錯"
  - "視覺化編輯器"
  - "逐步解說 [Windows Form], 偵錯"
ms.assetid: 1fd83ccd-3798-42fc-85a3-6cba99467387
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# 逐步解說：在設計階段偵錯自訂的 Windows Form 控制項
您在建立自訂控制項時，通常會發現需要對其設計階段行為進行偵錯。  如果您要撰寫自訂控制項的自訂設計工具，更是特別如此。  如需詳細資訊，請參閱[逐步解說：建立利用 Visual Studio 設計階段功能的 Windows Form 控制項](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md)。  
  
 您可以使用 Visual Studio 偵錯自訂控制項，就像偵錯任何其他 .NET Framework 類別 \(Class\) 一樣。  兩者的差異在於，您將偵錯個別的 Visual Studio 執行個體，此執行個體會執行自訂控制項的程式碼。  
  
 逐步解說將說明的工作包括：  
  
-   建立 Windows Form 專案以裝載自訂控制項  
  
-   建立控制項程式庫專案  
  
-   加入屬性至自訂控制項  
  
-   加入自訂控制項至主表單  
  
-   設定設計階段偵錯的專案  
  
-   在設計階段偵錯自訂控制項  
  
 當您完成時，便會對偵錯自訂控制項的設計階段行為需要的工作有所了解。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## 建立專案  
 首先建立應用程式物件。  您將會使用這個專案來建置裝載自訂控制項的應用程式。  
  
#### 若要建立專案  
  
-   建立稱為 "DebuggingExample" 的 Windows 應用程式專案。  如需詳細資訊，請參閱 [How to: Create a Windows Application Project](http://msdn.microsoft.com/zh-tw/b2f93fed-c635-4705-8d0e-cf079a264efa)。  
  
## 建立控制項程式庫專案  
 下一步便是建立控制項程式庫專案，並設定自訂控制項。  
  
#### 若要建立控制項程式庫專案  
  
1.  加入 \[**Windows 控制項程式庫**\] 專案至方案。  
  
2.  將新的 \[**使用者控制項**\] 加入至 DebugControlLibrary 專案。  如需詳細資訊，請參閱 [NIB:How to: Add New Project Items](http://msdn.microsoft.com/zh-tw/63d3e16b-de6e-4bb5-a0e3-ecec762201ce)。  為新的原始程式檔 \(Source File\) 提供主檔名 "DebugControl"。  
  
3.  使用 \[**方案總管**\] 刪除具有主檔名 "`UserControl1`" 的程式碼檔，藉此刪除專案的預設控制項。  如需詳細資訊，請參閱 [NIB:How to: Remove, Delete, and Exclude Items](http://msdn.microsoft.com/zh-tw/6dffdc86-29c8-4eff-bcd8-e3a0dd9e9a73)。  
  
4.  建置方案。  
  
## 檢查點  
 在這個檢查點時，可以在 \[**工具箱**\] 中看見自訂控制項。  
  
#### 若要檢查進度  
  
-   找到名為 \[**DebugControlLibrary 元件**\] 的新索引標籤，然後按一下加以選取。  當它開啟時，您會看見控制項被列為 \[**DebugControl**\]，且旁邊顯示預設圖示。  
  
## 加入屬性至自訂控制項  
 若要示範自訂控制項的程式碼執行於設計階段，您會加入屬性，並在實作屬性的程式碼中設定中斷點。  
  
#### 若要將屬性加入至自訂控制項  
  
1.  開啟 \[**程式碼編輯器**\] 中的 \[**DebugControl**\]。  加入下列程式碼至類別定義：  
  
    ```vb  
    Private demoStringValue As String = Nothing  
    <BrowsableAttribute(true)>  
    Public Property DemoString() As String  
  
        Get  
            Return Me.demoStringValue  
        End Get  
  
        Set(ByVal value As String)  
            Me.demoStringValue = value  
        End Set  
  
    End Property  
    ```  
  
    ```csharp  
    private string demoStringValue = null;  
    [Browsable(true)]  
    public string DemoString  
    {  
        get  
        {  
            return this.demoStringValue;  
        }  
        set  
        {  
            demoStringValue = value;  
        }  
    }  
    ```  
  
2.  建置方案。  
  
## 加入自訂控制項至主表單  
 若要偵錯自訂控制項的設計階段行為，您要將自訂控制項類別的執行個體放置在主表單上。  
  
#### 若要加入自訂控制項至主表單  
  
1.  在 "DebuggingExample" 專案中開啟 \[**Windows Form 設計工具**\] 的 Form1。  
  
2.  在 \[**工具箱**\] 中開啟 \[**DebugControlLibrary 元件**\] 索引標籤，並將 \[**DebugControl**\] 執行個體拖曳至表單上。  
  
3.  在 \[**屬性**\] 視窗中尋找 `DemoString` 自訂屬性。  請注意，您可以像對待任何其他屬性一樣，變更該屬性的值。  同時也要注意，當選取了 `DemoString` 屬性時，屬性的描述字串會出現在 \[**屬性**\] 視窗的底部。  
  
## 設定專案進行設計階段偵錯  
 若要偵錯自訂控制項的設計階段行為，您必須對執行自訂控制項程式碼的個別 Visual Studio 執行個體進行偵錯。  
  
#### 若要設定設計階段偵錯的專案  
  
1.  以滑鼠右鍵按一下 \[**方案總管**\] 中的 \[**DebugControlLibrary**\] 專案，然後選取 \[**屬性**\]。  
  
2.  在 \[**DebugControlLibrary**\] 屬性工作表中選取 \[**偵錯**\] 索引標籤。  
  
     在 \[**起始動作**\] 區段中選取 \[**起始外部程式**\]。  您將會偵錯個別的 Visual Studio 執行個體，所以請按一下省略 \(![VisualStudioEllipsesButton 螢幕擷取畫面](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\) 按鈕，以瀏覽 Visual Studio IDE。  可執行檔的名稱為 **devenv.exe**，如果您安裝至預設位置，其路徑就會是 %programfiles%\\Microsoft Visual Studio 9.0\\Common7\\IDE\\devenv.exe。  
  
3.  按一下 \[**確定**\] 以關閉對話方塊。  
  
4.  以滑鼠右鍵按一下 \[**DebugControlLibrary**\] 專案並選取 \[**設定為啟始專案**\] 以啟用這個偵錯設定。  
  
## 在設計階段偵錯自訂控制項  
 現在您已準備好在自訂控制項執行於設計階段時，對它進行偵錯。  當您啟動偵錯工作階段時，將會建立新的 Visual Studio 執行個體，且您將使用它來載入 "DebuggingExample" 方案。  當您開啟 \[**Form 設計工具**\] 中的 Form1 時，會建立自訂控制項的執行個體並開始執行。  
  
#### 若要在設計階段偵錯自訂控制項  
  
1.  開啟 \[**程式碼編輯器**\] 中的 \[**DebugControl**\] 原始程式檔，並在 `DemoString` 屬性的 `Set` 存取子上放置中斷點。  
  
2.  按 F5 以啟動偵錯工作階段。  請注意，會建立新的 Visual Studio 執行個體。  您能夠以兩種方式來區分執行個體：  
  
    -   偵錯執行個體在標題列中具有 \[**執行**\] 字詞  
  
    -   偵錯執行個體停用 \[**偵錯**\] 工具列上的 \[**啟動**\] 按鈕  
  
     您的中斷點是設定在偵錯執行個體中。  
  
3.  在新的 Visual Studio 執行個體中開啟 "DebuggingExample" 方案。  您可以輕易地找到方案，方法是從 \[**檔案**\] 功能表中選取 \[**最近使用的專案**\]。  "DebuggingExample.sln" 方案檔會被列為最近使用的檔案。  
  
4.  開啟 \[**Form 設計工具**\] 中的 Form1，並選取 \[**DebugControl**\] 控制項。  
  
5.  變更 `DemoString` 屬性值。  請注意，當您認可變更時，Visual Studio 的偵錯執行個體會需要焦點，且執行會停止在中斷點上。  您可以透過屬性存取子逐步執行，就像處理任何其他程式碼一樣。  
  
6.  完成偵錯工作階段時，可以關閉 Visual Studio 的裝載執行個體或按一下偵錯執行個體中的 \[**停止偵錯**\] 按鈕，藉此結束。  
  
## 後續步驟  
 現在您已經可以在設計階段偵錯自訂控制項，其他還有許多擴充控制項與 Visual Studio IDE 互動的可能性。  
  
-   您可以使用 <xref:System.ComponentModel.Component> 類別的 <xref:System.ComponentModel.Component.DesignMode%2A> 屬性來撰寫只會在設計階段執行的程式碼。  如需詳細資訊，請參閱 <xref:System.ComponentModel.Component.DesignMode%2A>。  
  
-   有數種屬性 \(Attribute\) 可以套用至控制項的屬性 \(Property\)，以管理自訂控制項和設計工具的互動。  您可以在 <xref:System.ComponentModel?displayProperty=fullName> 命名空間中找到這些屬性 \(Attribute\)。  
  
-   您可以撰寫自訂控制項的自訂設計工具。  這樣您在使用 Visual Studio 所公開 \(Expose\) 的可延伸設計工具基礎結構進行設計時，便可擁有完全的掌控。  如需詳細資訊，請參閱[逐步解說：建立利用 Visual Studio 設計階段功能的 Windows Form 控制項](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md)。  
  
## 請參閱  
 [逐步解說：建立利用 Visual Studio 設計階段功能的 Windows Form 控制項](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md)   
 [How to: Access Design\-Time Services](../Topic/How%20to:%20Access%20Design-Time%20Services.md)   
 [How to: Access Design\-Time Support in Windows Forms](../Topic/How%20to:%20Access%20Design-Time%20Support%20in%20Windows%20Forms.md)