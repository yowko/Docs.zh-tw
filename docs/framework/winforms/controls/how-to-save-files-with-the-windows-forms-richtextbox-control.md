---
title: 如何：使用 Windows Form RichTextBox 控制項儲存檔案
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
ms.openlocfilehash: c50b2f3309c1f811b29e824327a709e2cc4bd791
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33536191"
---
# <a name="how-to-save-files-with-the-windows-forms-richtextbox-control"></a>如何：使用 Windows Form RichTextBox 控制項儲存檔案
Windows Form<xref:System.Windows.Forms.RichTextBox>控制項可以撰寫會在幾種格式之一顯示的資訊：  
  
-   純文字  
  
-   Unicode 純文字  
  
-   Rtf 格式 (RTF)  
  
-   RTF 以空格取代 OLE 物件  
  
-   OLE 物件的文字表示的純文字  
  
 若要儲存檔案時，呼叫<xref:System.Windows.Forms.RichTextBox.SaveFile%2A>方法。 您也可以使用**SaveFile**方法，將資料儲存至資料流。 如需詳細資訊，請參閱<xref:System.Windows.Forms.RichTextBox.SaveFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>。  
  
### <a name="to-save-the-contents-of-the-control-to-a-file"></a>若要將控制項的內容儲存至檔案  
  
1.  判斷要儲存之檔案的路徑。  
  
     若要在真實世界應用程式中這樣做，您通常會使用<xref:System.Windows.Forms.SaveFileDialog>元件。 如需概觀，請參閱[SaveFileDialog 元件概觀](../../../../docs/framework/winforms/controls/savefiledialog-component-overview-windows-forms.md)。  
  
2.  呼叫<xref:System.Windows.Forms.RichTextBox.SaveFile%2A>方法<xref:System.Windows.Forms.RichTextBox>控制項，指定要儲存的檔案和 （選擇性） 的檔案類型。 如果您呼叫具有檔案名稱做為其唯一的引數的方法時，檔案會儲存為 RTF。 若要指定其他檔案類型，請呼叫以 <xref:System.Windows.Forms.RichTextBoxStreamType> 列舉值為其第二個引數的方法。  
  
     在下列範例中，設定路徑的 rtf 文字檔案位置是**我的文件**資料夾。 使用這個位置是因為您可以假設執行 Windows 作業系統的大部分電腦都會包含此資料夾。 選擇此位置也可讓使用者以最少的系統存取層級可安全地執行應用程式。 以下範例假設的表單具有<xref:System.Windows.Forms.RichTextBox>已經加入的控制項。  
  
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
    >  如果檔案不存在，此範例就會建立新的檔案。 如果必須建立檔案的應用程式，則該應用程式需要資料夾的建立權限。 您可以使用存取控制清單來設定權限。 如果檔案已經存在，應用程式只需要寫入權，較小者的權限。 可能的話，它是更安全，在部署期間，建立檔案並只授與讀取權限到單一檔案，而建立資料夾的存取。 此外，將資料寫入使用者資料夾，而不是根資料夾或 Program Files 資料夾，也更加安全。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.RichTextBox.SaveFile%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.RichTextBox>  
 [RichTextBox 控制項](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [在 Windows Forms 上使用的控制項](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
