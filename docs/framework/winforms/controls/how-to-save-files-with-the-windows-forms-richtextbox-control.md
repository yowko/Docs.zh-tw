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
ms.openlocfilehash: c5d88e4942d96ee12e8b9f40156090c874386668
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046257"
---
# <a name="how-to-save-files-with-the-windows-forms-richtextbox-control"></a>作法：使用 Windows Forms RichTextBox 控制項儲存檔案

Windows Forms <xref:System.Windows.Forms.RichTextBox>控制項可以用數種格式的其中一種來撰寫所顯示的資訊:

- 純文字

- Unicode 純文字

- Rtf 格式 (RTF)

- 以空格取代 OLE 物件的 RTF

- 純文字, 具有 OLE 物件的文字標記法

若要儲存檔案, 請<xref:System.Windows.Forms.RichTextBox.SaveFile%2A>呼叫方法。 您也可以使用**SaveFile**方法, 將資料儲存至資料流程。 如需詳細資訊，請參閱 <xref:System.Windows.Forms.RichTextBox.SaveFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>。

### <a name="to-save-the-contents-of-the-control-to-a-file"></a>將控制項的內容儲存至檔案

1. 決定要儲存之檔案的路徑。

    若要在真實世界的應用程式中執行這項操作, 您<xref:System.Windows.Forms.SaveFileDialog>通常會使用元件。 如需總覽, 請參閱[SaveFileDialog 元件總覽](savefiledialog-component-overview-windows-forms.md)。

2. 呼叫控制項<xref:System.Windows.Forms.RichTextBox>的方法,並指定要儲存的檔案和選擇性<xref:System.Windows.Forms.RichTextBox.SaveFile%2A>的檔案類型。 如果您使用檔案名做為唯一的引數來呼叫方法, 檔案將會儲存為 RTF。 若要指定其他檔案類型，請呼叫以 <xref:System.Windows.Forms.RichTextBoxStreamType> 列舉值為其第二個引數的方法。

    在下列範例中, 為 rtf 檔案的位置設定的路徑為 [**我的文件**] 資料夾。 因為您可以假設大部分執行 Windows 作業系統的電腦都包含此資料夾, 所以會使用這個位置。 選擇此位置也可讓具有最低系統存取層級的使用者安全地執行應用程式。 下列範例假設已加入<xref:System.Windows.Forms.RichTextBox>控制項的表單。

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
    > 如果檔案不存在，此範例就會建立新的檔案。 如果應用程式需要建立檔案, 該應用程式需要建立該資料夾的存取權。 您可以使用存取控制清單來設定權限。 如果檔案已經存在, 則應用程式只需要寫入權限, 這是較小的許可權。 可能的話, 在部署期間建立檔案會比較安全, 而且只會授與單一檔案的讀取權限, 而不是建立資料夾的存取權。 此外，將資料寫入使用者資料夾，而不是根資料夾或 Program Files 資料夾，也更加安全。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.RichTextBox.SaveFile%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.RichTextBox>
- [RichTextBox 控制項](richtextbox-control-windows-forms.md)
- [在 Windows Forms 上使用的控制項](controls-to-use-on-windows-forms.md)
