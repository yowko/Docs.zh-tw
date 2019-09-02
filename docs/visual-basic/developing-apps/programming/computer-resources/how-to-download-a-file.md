---
title: 作法：在 Visual Basic 中下載檔案
ms.date: 07/20/2015
helpviewer_keywords:
- downloading Internet resources [Visual Basic], files
- downloading files [Visual Basic]
- remote computers [Visual Basic], downloading from
- files [Visual Basic], downloading
- files [Visual Basic], transferring
ms.assetid: ac479f81-c0e2-4b99-af73-217f446b73da
ms.openlocfilehash: 4dd45ef70dbe3b1949e6d787748bbb27bb88d52c
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046618"
---
# <a name="how-to-download-a-file-in-visual-basic"></a>作法：在 Visual Basic 中下載檔案

<xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A> 方法可以用來下載遠端檔案，並將它儲存到特定位置。 如果 `ShowUI` 參數設定為 `True`，則會顯示對話方塊以顯示下載進度，並允許使用者取消作業。 根據預設，不會覆寫具有相同名稱的現有檔案；如果您想要覆寫現有檔案，請將 `overwrite` 參數設定為 `True`。

以下條件可能會造成例外狀況：

- 磁碟機名稱無效 (<xref:System.ArgumentException>)。

- 未提供必要驗證 (<xref:System.UnauthorizedAccessException> 或 <xref:System.Security.SecurityException>)。

- 伺服器在指定的 `connectionTimeout` 內沒有回應 (<xref:System.TimeoutException>)。

- 要求被網站拒絕 (<xref:System.Net.WebException>)。

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

> [!IMPORTANT]
> 請勿根據檔案名稱來判斷檔案內容。 例如，檔案 Form1.vb 可能不是 Visual Basic 來源檔案。 在應用程式中使用這些資料之前，請先驗證所有輸入值。 檔案內容可能與預期不同，並從檔案讀取資料的方法會失敗。

### <a name="to-download-a-file"></a>下載檔案

- 使用 `DownloadFile` 方法下載檔案，並以字串或 URI 形式指定目標檔案的位置，以及指定要儲存檔案的位置。 此範例會從 `http://www.cohowinery.com/downloads` 下載 `WineList.txt` 檔案，然後將它儲存至 `C:\Documents and Settings\All Users\Documents`：

  [!code-vb[VbResourceTasks#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#9)]

### <a name="to-download-a-file-specifying-a-time-out-interval"></a>下載檔案並指定逾時間隔

- 使用 `DownloadFile` 方法下載檔案，並以字串或 URI 形式指定目標檔案的位置、指定要儲存檔案的位置，以及指定以毫秒為單位的逾時間隔 (預設值為 1000)。 此範例會從 `http://www.cohowinery.com/downloads` 下載 `WineList.txt` 檔案，然後將它儲存至 `C:\Documents and Settings\All Users\Documents`，並指定 500 毫秒的逾時間隔：

  [!code-vb[VbResourceTasks#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#10)]

### <a name="to-download-a-file-supplying-a-user-name-and-password"></a>下載檔案並提供使用者名稱和密碼

- 使用 `DownLoadFile` 方法下載檔案，並以字串或 URI 形式指定目標檔案的位置，以及指定要儲存檔案、使用者名稱和密碼的位置。 此範例會從 `http://www.cohowinery.com/downloads` 下載 `WineList.txt` 檔案，然後將它儲存至具有使用者名稱 `anonymous` 和空白密碼的 `C:\Documents and Settings\All Users\Documents`。

  [!code-vb[VbResourceTasks#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#11)]

  > [!IMPORTANT]
  > `DownLoadFile` 方法所使用的 FTP 通訊協定會以純文字傳送資訊 (包括密碼)，不應用於傳輸機密資訊。

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.Devices.Network>
- <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A>
- [如何：上傳檔案](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-upload-a-file.md)
- [如何：剖析檔案路徑](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
