---
title: "無法寫入輸出檔案 '<filename>': <error>"
ms.date: 07/20/2015
f1_keywords:
- vbc31019
- bc31019
helpviewer_keywords:
- BC31019
ms.assetid: 0845b245-11bb-46fd-95ca-f6cef3c318ef
ms.openlocfilehash: 087735722fcd4dd789e25aacf6eeefffb490dac5
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198198"
---
# <a name="unable-to-write-to-output-file-filename-error"></a>無法寫入輸出檔 '\<filename > '： \<錯誤 >
建立檔案時發生問題。  
  
 無法開啟輸出檔案以供寫入。 檔案 (或包含檔案的資料夾) 可能已由另一個處理序以獨佔方式開啟使用，或是其可能設定了唯讀屬性。  
  
 以獨佔方式開啟檔案的常見狀況有：  
  
- 應用程式已在執行中，且正在使用其檔案。 若要解決此問題，請確定應用程式不在執行中。  
  
- 另一個應用程式已開啟該檔案。 若要解決此問題，請確定沒有其他應用程式正在存取檔案。 您不一定能顯而易見地分辨出是哪個應用程式在存取您的檔案；在這種情況下，重新啟動電腦可能是終止該應用程式最容易的方法。  
  
 即使是其中一個專案輸出檔被標為唯讀，都會擲回這個例外狀況。  
  
 **錯誤識別碼：** BC31019  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 再次編譯程式，看看錯誤是否重複發生。  
  
2. 如果錯誤繼續發生，請儲存您的工作並重新啟動 Visual Studio。  
  
3. 如果錯誤繼續發生，請重新啟動電腦。  
  
4. 如果錯誤重複發生，請重新安裝 Visual Basic。  
  
5. 如果錯誤在重新安裝之後持續發生，請通知 Microsoft 產品支援服務。  
  
### <a name="to-check-file-attributes-in-file-explorer"></a>在檔案總管中檢查檔案屬性  
  
1. 開啟您感興趣的資料夾。  
  
2. 按一下 [ **Views** ] 圖示，然後選擇 [**詳細資料**]。  
  
3. 以滑鼠右鍵按一下資料行標頭，然後從下拉式清單中選擇 [**屬性**]。  
  
### <a name="to-change-the-attributes-of-a-file-or-folder"></a>變更檔案或資料夾的屬性  
  
1. 在 [檔案**管理器**] 中，以滑鼠右鍵按一下檔案或資料夾，然後選擇 [**屬性**]。  
  
2. 在 [**一般**] 索引標籤的 [**屬性**] 區段中，清除 [**唯讀**] 核取方塊。  
  
3. 按 [確定]。  
  
## <a name="see-also"></a>請參閱

- [告訴我們](/visualstudio/ide/feedback-options)
