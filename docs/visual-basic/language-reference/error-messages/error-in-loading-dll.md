---
title: 載入 DLL 時發生錯誤
ms.date: 07/20/2015
f1_keywords:
- vbrID48
ms.assetid: 4226cd1f-028c-477d-88a5-cb57f7e0cdc8
ms.openlocfilehash: fd2e425f2dd3f4127cd777d4a1f7ab9809de9d45
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409619"
---
# <a name="error-in-loading-dll-visual-basic"></a>載入 DLL 時發生錯誤 (Visual Basic)
動態連結程式庫（DLL）是在語句的子句中指定的程式庫 `Lib` `Declare` 。 此錯誤的可能原因包括：  
  
- 檔案不是 DLL 可執行檔。  
  
- 檔案不是 Microsoft Windows DLL。  
  
- DLL 參考另一個不存在的 DLL。  
  
- DLL 或參考的 DLL 不在路徑中指定的目錄中。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 如果檔案是原始程式檔，而不是 DLL 可執行檔，則必須編譯並連結至 DLL 可執行檔表單。  
  
- 如果檔案不是 Microsoft Windows DLL，請取得 Microsoft Windows 對等的。  
  
- 如果 DLL 參考另一個不存在的 DLL，請取得參考的 DLL 並使其可供使用。  
  
- 如果 DLL 或參考的 DLL 不在路徑所指定的目錄中，請將 DLL 移至參考的目錄。  
  
## <a name="see-also"></a>另請參閱

- [Declare Statement](../statements/declare-statement.md)
