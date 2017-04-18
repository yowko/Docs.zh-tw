---
title: "如何：使用 Windows Form RichTextBox 控制項儲存檔案 | Microsoft Docs"
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
  - ".rtf 檔案, 在 RichTextBox 控制項中儲存"
  - "範例 [Windows Form], 文字方塊"
  - "檔案, 與 RichTextBox 控制項一起儲存"
  - "RichTextBox 控制項 [Windows Form], 儲存檔案"
  - "RTF 檔案, 在 RichTextBox 控制項中儲存"
  - "儲存檔案"
  - "儲存檔案, RichTextBox 控制項"
  - "文字檔, 自 RichTextBox 控制項儲存"
ms.assetid: 4a58ec19-84d1-4383-9110-298c06adcfca
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 如何：使用 Windows Form RichTextBox 控制項儲存檔案
Windows Form <xref:System.Windows.Forms.RichTextBox> 控制項可寫入以下列幾種格式顯示的資訊：  
  
-   純文字  
  
-   Unicode 純文字  
  
-   RTF  
  
-   RTF，其中以空格代替 OLE 物件  
  
-   純文字加上 OLE 物件的文字表示  
  
 若要儲存檔案，請呼叫 <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> 方法。  您也可使用 **SaveFile** 方法來將資料儲存至資料流。  如需詳細資訊，請參閱 <xref:System.Windows.Forms.RichTextBox.SaveFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>。  
  
### 若要將控制項的內容儲存至檔案  
  
1.  決定要儲存檔案的路徑。  
  
     若要在實際應用程式中這麼做，您通常會使用 <xref:System.Windows.Forms.SaveFileDialog> 元件。  如需概觀說明，請參閱[SaveFileDialog 元件概觀](../../../../docs/framework/winforms/controls/savefiledialog-component-overview-windows-forms.md)。  
  
2.  呼叫 <xref:System.Windows.Forms.RichTextBox> 控制項的 <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> 方法，指定要儲存的檔案並選擇性地指定檔案類型。  如果您只使用檔名當做呼叫方法的唯一引數，就會將檔案儲存為 RTF。  若要指定其他檔案類型，請呼叫方法並將 <xref:System.Windows.Forms.RichTextBoxStreamType> 列舉型別的任一值當做第二個引數。  
  
     在以下範例中，為 RTF 檔位置設定的路徑為 \[**我的文件**\] 資料夾。  這個位置的使用，是因為您可假設大部分執行 Windows 作業系統的電腦，都會包含這個資料夾。  選擇這個位置也可讓使用者以最基本的系統存取層級，便可安全執行應用程式。  下列範例假設已將 <xref:System.Windows.Forms.RichTextBox> 控制項加入表單。  
  
    ```vb  
    Public Sub SaveFile()  
       ' You should replace the bold file name in the   
       ' sample below with a file name of your own choosing.  
       RichTextBox1.SaveFile(System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Testdoc.rtf", _  
          RichTextBoxStreamType.RichNoOleObjs)  
    End Sub  
  
    ```  
  
    ```csharp  
    public void SaveFile()  
    {  
       // You should replace the bold file name in the   
       // sample below with a file name of your own choosing.  
       // Note the escape character used (@) when specifying the path.  
       richTextBox1.SaveFile(System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Testdoc.rtf",  
          RichTextBoxStreamType.RichNoOleObjs);  
    }  
  
    ```  
  
    ```cpp  
    public:  
       void SaveFile()  
       {  
          // You should replace the bold file name in the   
          // sample below with a file name of your own choosing.  
          richTextBox1->SaveFile(String::Concat  
             (System::Environment::GetFolderPath  
             (System::Environment::SpecialFolder::Personal),  
             "\\Testdoc.rtf"), RichTextBoxStreamType::RichNoOleObjs);  
       }  
    ```  
  
    > [!IMPORTANT]
    >  如果檔案不存在，這個範例就會建立新檔案。  如果應用程式需要建立檔案，該應用程式就需要資料夾的建立權限。  使用權限是使用存取控制清單設定的。  如果檔案已經存在，應用程式只需要寫入權限，這是較小的權限。  若有可能，更為安全的做法是在部署期間建立檔案，並且只授與存取單一檔案的 Read 存取權，而不要授與存取資料夾的 Create 存取權。  此外，較安全的做法是將資料寫入使用者資料夾，而不要寫入根資料夾或 \[Program Files\] 資料夾。  
  
## 請參閱  
 <xref:System.Windows.Forms.RichTextBox.SaveFile%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.RichTextBox>   
 [RichTextBox 控制項](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)   
 [在 Windows Form 上使用的控制項](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)