---
title: "如何：將控制項加入至 Windows Form"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, adding to form
- controls [Windows Forms], adding
ms.assetid: 2af86001-9d62-4154-87fb-66db2c3cd9fd
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ab92f7a56173ec71642d0cc09f3f81e9859533b4
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-add-controls-to-windows-forms"></a>如何：將控制項加入至 Windows Form
大部分表單都設計成將控制項加入至表單的表面，以定義使用者介面 (UI)。 A*控制項*是用來顯示資訊或可接受使用者輸入表單上的元件。 如需將控制項的詳細資訊，請參閱[Windows Form 控制項](../../../../docs/framework/winforms/controls/index.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
### <a name="to-draw-a-control-on-a-form"></a>若要繪製控制項在表單上  
  
1.  開啟表單。 如需詳細資訊，請參閱[如何： 顯示 Windows Form 設計工具中](http://msdn.microsoft.com/library/bf3f1e5b-ea07-4529-85c6-6af3ded0cec5)。  
  
2.  在**工具箱**，按一下您想要新增至表單的控制項。  
  
3.  在表單中，按一下想要找出，控制項的左上角的位置並拖曳至想要找出控制項的右下角。  
  
     控制項會加入至表單，以指定的位置和大小。  
  
    > [!NOTE]
    >  每個控制項具有定義的預設大小。 您可以將控制項加入至您的表單控制項的預設大小中將它從**工具箱**至表單。  
  
### <a name="to-drag-a-control-to-a-form"></a>若要將控制項拖曳至表單  
  
1.  開啟表單。 如需詳細資訊，請參閱[如何： 顯示 Windows Form 設計工具中](http://msdn.microsoft.com/library/bf3f1e5b-ea07-4529-85c6-6af3ded0cec5)。  
  
2.  在**工具箱**，按一下您想要並將它拖曳至表單的控制項。  
  
     控制項會加入至表單，以預設大小的指定位置。  
  
    > [!NOTE]
    >  您可以按兩下中的控制項**工具箱**將它加入至表單的預設大小的左上角。  
  
     您也可以加入控制項動態表單在執行階段。 在下列程式碼範例中，<xref:System.Windows.Forms.TextBox>將控制項加入表單時<xref:System.Windows.Forms.Button>按一下控制項時。  
  
    > [!NOTE]
    >  下列程序需要具有的表單有**按鈕**控制項， `Button1`、 已放置在其上。  
  
### <a name="to-add-a-control-to-a-form-programmatically"></a>若要以程式設計方式將控制項加入表單  
  
1.  在方法中處理按鈕的`Click`事件表單的類別，如下所示將參考加入至您的控制項變數的插入程式碼內設定控制項的`Location`，並加入控制項。  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
       Dim MyText As New TextBox()  
       MyText.Location = New Point(25, 25)  
       Me.Controls.Add(MyText)  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)   
    {  
       TextBox myText = new TextBox();  
       myText.Location = new Point(25,25);  
       this.Controls.Add (myText);  
    }  
    ```  
  
    ```cpp  
    private:  
      System::Void button1_Click(System::Object ^  sender,  
        System::EventArgs ^  e)  
      {  
        TextBox ^ myText = gcnew TextBox();  
        myText->Location = Point(25,25);  
        this->Controls->Add(myText);  
      }  
    ```  
  
    > [!NOTE]
    >  您也可以加入程式碼以初始化控制項的其他屬性。  
  
    > [!IMPORTANT]
    >  您可能會藉由參考惡意公開本機電腦透過網路的安全性風險`UserControl`。 這只會考量使用者惡意破壞性的自訂控制項，且您不小心將其加入您專案的建立。  
  
## <a name="see-also"></a>請參閱  
 [Windows Forms 控制項](../../../../docs/framework/winforms/controls/index.md)  
 [排列 Windows Forms 上的控制項](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [操作說明：重新調整 Windows Forms 上控制項的大小](../../../../docs/framework/winforms/controls/how-to-resize-controls-on-windows-forms.md)  
 [操作說明：設定由 Windows Forms 控制項所顯示的文字](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)  
 [在 Windows Forms 上使用的控制項](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
