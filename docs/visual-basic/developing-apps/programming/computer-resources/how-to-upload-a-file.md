---
title: 作法：在 Visual Basic 中上傳檔案
ms.date: 07/20/2015
helpviewer_keywords:
- networks, uploading files
- files [Visual Basic], uploading
- uploading files [Visual Basic]
- UploadFile method [Visual Basic]
- My.Computer.Network.UploadFile method
ms.assetid: a8b37924-c523-4fd3-b5ca-cb0074df29cd
ms.openlocfilehash: 486351bc140a2bbf18bb8f85f761fc491f028bba
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58840349"
---
# <a name="how-to-upload-a-file-in-visual-basic"></a>作法：在 Visual Basic 中上傳檔案
<xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A> 方法可以用於上傳檔案，並將其存放到遠端位置。 如果 `ShowUI` 參數設定為 `True`，則會顯示對話方塊以顯示上傳進度，並允許使用者取消作業。  
  
### <a name="to-upload-a-file"></a>上傳檔案  
  
-   使用 `UploadFile` 方法來上傳檔案，並將來源檔案的位置和目標目錄位置指定為字串或 URI (統一資源識別項)。這個範例會將檔案 `Order.txt` 上傳到 `http://www.cohowinery.com/uploads.aspx`。  
  
     [!code-vb[VbResourceTasks#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#6)]  
  
### <a name="to-upload-a-file-and-show-the-progress-of-the-operation"></a>上傳檔案並顯示作業進度  
  
-   使用 `UploadFile` 方法來上傳檔案，並將來源檔案的位置和目標目錄位置指定為字串或 URI。 這個範例會在未提供使用者名稱或密碼的情況下將 `Order.txt` 檔案上傳至 `http://www.cohowinery.com/uploads.aspx`、顯示上傳進度，並具有 500 毫秒的逾時間隔。  
  
     [!code-vb[VbResourceTasks#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#7)]  
  
### <a name="to-upload-a-file-supplying-a-user-name-and-password"></a>上傳檔案並提供使用者名稱和密碼  
  
-   使用 `UploadFile` 方法來上傳檔案，並將來源檔案的位置和目標目錄位置指定為字串或 URI，以及指定使用者名稱和密碼。 這個範例會將 `Order.txt` 檔案上傳至 `http://www.cohowinery.com/uploads.aspx`，並提供使用者名稱 `anonymous` 和空白密碼。  
  
     [!code-vb[VbResourceTasks#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#8)]  
  
## <a name="robust-programming"></a>穩固程式設計  
 下列條件可能會擲回例外狀況：  
  
-   本機檔案路徑無效 (<xref:System.ArgumentException>)。  
  
-   驗證失敗 (<xref:System.Security.SecurityException>)。  
  
-   連線逾時 (<xref:System.TimeoutException>)。  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A>
- [如何：下載檔案](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-download-a-file.md)
- [如何：剖析檔案路徑](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
