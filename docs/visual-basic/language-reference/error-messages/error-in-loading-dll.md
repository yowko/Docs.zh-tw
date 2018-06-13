---
title: 載入 DLL 時發生錯誤 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID48
ms.assetid: 4226cd1f-028c-477d-88a5-cb57f7e0cdc8
ms.openlocfilehash: ac21c4d52b248025ee26bac3e511bb5b0a0b668e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33584679"
---
# <a name="error-in-loading-dll-visual-basic"></a>載入 DLL 時發生錯誤 (Visual Basic)
動態連結程式庫 (DLL) 是程式庫中指定`Lib`子句`Declare`陳述式。 這項錯誤的可能原因包括：  
  
-   檔案不是可執行檔的 DLL。  
  
-   檔案不是 Microsoft Windows DLL。  
  
-   DLL 會參考不存在的另一個 DLL。  
  
-   DLL 或參考的 DLL 不在路徑中指定的目錄。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   如果是檔案的原始程式文字檔案，因此不 DLL 的可執行檔，它必須編譯並連結到 DLL 可執行檔格式。  
  
-   如果不是 Microsoft Windows DLL 檔案，取得對等的 Microsoft Windows。  
  
-   如果 DLL 參考不存在的另一個 DLL 時，取得參考的 DLL，並將其提供。  
  
-   如果 DLL 或參考的 DLL 不指定路徑的目錄中，請將 DLL 移到參考的目錄。  
  
## <a name="see-also"></a>另請參閱  
 [Declare 陳述式](../../../visual-basic/language-reference/statements/declare-statement.md)
