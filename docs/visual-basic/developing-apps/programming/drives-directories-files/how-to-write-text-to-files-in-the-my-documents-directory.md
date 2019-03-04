---
title: 作法：在 Visual Basic 中將文字寫入 [我的文件] 目錄中的檔案
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- examples [Visual Basic], text files
- writing to files [Visual Basic], in My Documents
ms.assetid: 1c726124-781d-4976-9baa-ed46814ff3fe
ms.openlocfilehash: 147dad822a8bc8b8e9692b88f6b498f841bac1fa
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56966745"
---
# <a name="how-to-write-text-to-files-in-the-my-documents-directory-in-visual-basic"></a>HOW TO：在 Visual Basic 中將文字寫入 [我的文件] 目錄中的檔案
`My.Computer.FileSystem.SpecialDirectories` 物件可讓您存取特殊目錄，例如 [我的文件] 目錄。  
  
## <a name="procedure"></a>程序  
  
#### <a name="to-write-new-text-files-in-the-my-documents-directory"></a>將新文字檔寫入 [我的文件] 目錄中  
  
1.  使用 `My.Computer.FileSystem.SpecialDirectories.MyDocuments` 屬性，來提供路徑。  
  
     [!code-vb[VbFileIOWrite#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#1)]  
  
2.  使用 `WriteAllText` 方法，將文字寫入指定的檔案。  
  
     [!code-vb[VbVbcnMyFileSystem#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#14)]  
  
## <a name="example"></a>範例  
 [!code-vb[VbFileIOWrite#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#2)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 請將 `test.txt` 取代為您想要寫入之檔案的名稱。  
  
## <a name="robust-programming"></a>穩固程式設計  
 這個程式碼會重新擲回將文字寫入檔案時可能發生的所有例外狀況。 使用 [OpenFileDialog](../../../../framework/winforms/controls/openfiledialog-component-windows-forms.md) 和 [SaveFileDialog](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md) 元件這類 Windows Forms 控制項以將使用者選項限制為有效檔案名稱，即可減少例外狀況的可能性。 不過，使用這些控制項並不容易。 在使用者選取檔案的時間與程式碼執行的時間之間，可以變更檔案系統。 因此，使用檔案時，幾乎一律都需要進行例外狀況處理。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 如果要在部分信任內容中執行，則程式碼可能會因權限不足而擲回例外狀況。 如需詳細資訊，請參閱[程式碼存取安全性基本概念](../../../../framework/misc/code-access-security-basics.md)。  
  
 這個範例會建立新的檔案。 如果應用程式需要建立檔案，該應用程式就需要資料夾的 [建立] 權限。 您可以使用存取控制清單來設定權限。 如果檔案已經存在，則應用程式只需要 [寫入] 權限，這是較小的權限。 若有可能，更為安全的做法是在部署期間建立檔案，並且只授與單一檔案的 [讀取] 權限，而不授與資料夾的 [建立] 權限。 此外，將資料寫入使用者資料夾，而不是根資料夾或 **Program Files** 資料夾，也更加安全。 如需詳細資訊，請參閱 [ACL 技術概觀](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229742(v=vs.100))。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.IO.Path.Combine%2A?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>
