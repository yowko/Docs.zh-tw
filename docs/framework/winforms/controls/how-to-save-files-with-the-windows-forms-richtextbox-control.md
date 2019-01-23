---
title: HOW TO：使用 Windows Forms RichTextBox 控制項儲存檔案
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- saving files
- RTF files [Windows Forms], saving in RichTextBox control
- examples [Windows Forms], text boxes
- saving files [Windows Forms], RichTextBox control
- files [Windows Forms], saving with RichTextBox control
- RichTextBox control [Windows Forms], saving files
- .rtf files [Windows Forms], saving in RichTextBox control
- text files [Windows Forms], saving from RichTextBox control
ms.assetid: 4a58ec19-84d1-4383-9110-298c06adcfca
ms.openlocfilehash: 739cc33df873ef2c8ec7a2f5eaf867abadb8da75
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54539775"
---
# <a name="how-to-save-files-with-the-windows-forms-richtextbox-control"></a>HOW TO：使用 Windows Forms RichTextBox 控制項儲存檔案
Windows Form<xref:System.Windows.Forms.RichTextBox>控制項可以撰寫會在幾種格式之一中顯示的資訊：  
  
-   純文字  
  
-   Unicode 純文字  
  
-   Rich Text Format (RTF)  
  
-   RTF 空格 OLE 物件的位置  
  
-   OLE 物件的文字表示的純文字  
  
 若要儲存檔案，請呼叫<xref:System.Windows.Forms.RichTextBox.SaveFile%2A>方法。 您也可以使用**SaveFile**方法，將資料儲存至資料流。 如需詳細資訊，請參閱<xref:System.Windows.Forms.RichTextBox.SaveFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>。  
  
### <a name="to-save-the-contents-of-the-control-to-a-file"></a>將控制項的內容儲存至檔案  
  
1.  判斷要儲存之檔案的路徑。  
  
     若要在真實世界應用程式中這樣做，您通常會使用<xref:System.Windows.Forms.SaveFileDialog>元件。 如需概觀，請參閱[SaveFileDialog 元件概觀](../../../../docs/framework/winforms/controls/savefiledialog-component-overview-windows-forms.md)。  
  
2.  呼叫<xref:System.Windows.Forms.RichTextBox.SaveFile%2A>方法的<xref:System.Windows.Forms.RichTextBox>控制項，指定要儲存的檔案和選擇性的檔案類型。 如果您呼叫具有某檔案名稱為其唯一引數的方法，該檔案會儲存為 RTF。 若要指定其他檔案類型，請呼叫以 <xref:System.Windows.Forms.RichTextBoxStreamType> 列舉值為其第二個引數的方法。  
  
     在下列範例中，將路徑設為 rtf 文字檔案的位置**我的文件**資料夾。 因為您可以假設大部分執行 Windows 作業系統的電腦將會包含此資料夾，會使用此位置。 選擇此位置也可讓具有最少的系統存取層級的使用者安全地執行應用程式。 下列範例假設表單<xref:System.Windows.Forms.RichTextBox>已經加入的控制項。  
  
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
    >  如果檔案不存在，此範例就會建立新的檔案。 如果應用程式需要建立檔案，該應用程式會需要建立存取資料夾。 您可以使用存取控制清單來設定權限。 如果檔案已經存在，則應用程式必須只寫入權限的較低的權限。 可能的話，它是在部署期間，建立檔案和只授與讀取權限，以單一檔案，而非建立資料夾的存取更安全。 此外，將資料寫入使用者資料夾，而不是根資料夾或 Program Files 資料夾，也更加安全。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Forms.RichTextBox.SaveFile%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.RichTextBox>
- [RichTextBox 控制項](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)
- [在 Windows Forms 上使用的控制項](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
