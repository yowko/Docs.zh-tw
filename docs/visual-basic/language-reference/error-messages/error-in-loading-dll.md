---
title: 載入 DLL 時發生錯誤
ms.date: 07/20/2015
f1_keywords:
- vbrID48
ms.assetid: 4226cd1f-028c-477d-88a5-cb57f7e0cdc8
ms.openlocfilehash: 35733fe2e20d46207f6cfdaee32f6559fceed6eb
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874386"
---
# <a name="error-in-loading-dll-visual-basic"></a>載入 DLL 時發生錯誤 (Visual Basic)

動態連結程式庫 (DLL) 是在語句的子句中指定的程式庫 `Lib` `Declare` 。 此錯誤的可能原因包括：  
  
- 檔案不是 DLL 可執行檔。  
  
- 檔案不是 Microsoft Windows DLL。  
  
- DLL 參考不存在的另一個 DLL。  
  
- DLL 或參考的 DLL 不在路徑中指定的目錄中。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 如果檔案是來源文字檔，而不是 DLL 可執行檔，則必須將它編譯並連結至 DLL 可執行檔表單。  
  
- 如果檔案不是 Microsoft Windows DLL，請取得 Microsoft Windows 對等專案。  
  
- 如果 DLL 參考不存在的另一個 DLL，請取得參考的 DLL，並使其可供使用。  
  
- 如果 DLL 或參考的 DLL 不在路徑所指定的目錄中，請將 DLL 移至參考的目錄。  
  
## <a name="see-also"></a>另請參閱

- [Declare Statement](../statements/declare-statement.md)
