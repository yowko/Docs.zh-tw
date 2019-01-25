---
title: Windows Form 設計工具的設計階段錯誤
ms.date: 03/30/2017
f1_keywords:
- DTELErrorList
- WhyDTELPage
helpviewer_keywords:
- errors [Windows Forms Designer]
- design-time errors [Windows Forms Designer]
ms.assetid: ad408380-825a-46d8-9a4a-531b130b88ce
ms.openlocfilehash: 26f57b039b8e2fb3c56af926eeb63dc3c4c33b55
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54542401"
---
# <a name="design-time-errors-in-the-windows-forms-designer"></a>Windows Form 設計工具的設計階段錯誤
本主題說明當 Windows Forms 設計工具載入失敗時，Microsoft Visual Studio 中所出現的設計階段錯誤清單的意義與用法。 如果出現此錯誤清單，您不應該將它視為是設計工具中的錯誤，而是協助您更正程式碼中的錯誤。  
  
 在基本上了解此錯誤清單會提供錯誤的詳細資訊並建議可能的解決方案，將有助於您偵錯應用程式。  
  
## <a name="the-design-time-error-list-interface"></a>設計階段錯誤清單介面  
 如果 Windows Forms 設計工具載入失敗，錯誤清單會出現在設計工具中。 錯誤依分類分組。 比方說，如果您有四個未宣告的變數執行個體，這些會分組到相同的錯誤分類。 每個錯誤分類包含摘要說明此錯誤的簡短描述。  
  
 您可以按一下錯誤分類標題，或按一下展開/摺疊 > 形箭號，以展開或摺疊錯誤分類。 當您展開錯誤分類時，將會顯示下列額外說明︰  
  
-   此錯誤的執行個體。  
  
-   此錯誤的說明。  
  
-   此錯誤的相關論壇文章。  
  
### <a name="instances-of-this-error"></a>此錯誤的執行個體  
 額外說明會列出目前專案中該錯誤的所有執行個體。 許多錯誤包括確切的位置，格式如下︰[專案名稱] [表單名稱] 行︰[行號]資料行︰[資料行號碼]。 [移至程式碼] 連結將帶您前往程式碼中發生錯誤的位置。  
  
 如果錯誤有關聯的呼叫堆疊，您可以按一下 [呼叫堆疊顯示] 連結，進一步展開錯誤以顯示呼叫堆疊。 檢查堆疊可以提供寶貴的偵錯資訊。 例如，您可以追蹤發生錯誤之前所呼叫的函式。 您可以選取呼叫堆疊以複製並儲存。  
  
> [!NOTE]
>  在 Visual Basic 中，設計階段錯誤清單不會顯示一個以上的錯誤，但可能顯示相同錯誤的多個執行個體。 在 Visual C++ 中，錯誤沒有 [移至程式碼] 連結/行號連結。  
  
### <a name="help-with-this-error"></a>此錯誤的說明  
 如果錯誤包含關聯 MSDN 說明主題的連結，則額外說明會包含說明主題的連結。 當您按一下連結時，關聯的說明主題會出現在 Visual Studio 中。  
  
### <a name="forum-posts-about-this-error"></a>此錯誤的相關論壇文章  
 額外說明包含與錯誤相關之 MSDN 論壇文章的連結。 系統是根據錯誤訊息的字串來搜尋論壇。 您也可以嘗試搜尋下列論壇︰  
  
-   [Windows Forms 設計工具論壇](https://go.microsoft.com/fwlink/?LinkId=203524)  
  
-   [Windows Forms 論壇](https://go.microsoft.com/fwlink/?LinkId=203523)  
  
### <a name="ignore-and-continue"></a>忽略並繼續  
 您可以選擇忽略錯誤狀況並繼續載入設計工具。 選擇此動作可能會導致非預期的行為。 例如，控制項可能不會出現在設計介面上。  
  
## <a name="see-also"></a>另請參閱
- [疑難排解設計階段開發](https://msdn.microsoft.com/library/e048d08e-fa7c-4be8-b238-4abaa199a0a6)
- [針對控制項和元件撰寫進行疑難排解](../../../../docs/framework/winforms/controls/troubleshooting-control-and-component-authoring.md)
- [在設計階段開發 Windows Forms 控制項](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)
- [Windows Forms 設計工具錯誤訊息](https://msdn.microsoft.com/library/cf610bf4-5fe4-471c-bce7-6a05ece07bd2)
