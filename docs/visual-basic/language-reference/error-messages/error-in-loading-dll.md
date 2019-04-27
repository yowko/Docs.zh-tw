---
title: 載入 DLL 時發生錯誤 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID48
ms.assetid: 4226cd1f-028c-477d-88a5-cb57f7e0cdc8
ms.openlocfilehash: c3f88a5a3c37c89d23055aa413957b2add38ed67
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61803463"
---
# <a name="error-in-loading-dll-visual-basic"></a>載入 DLL 時發生錯誤 (Visual Basic)
動態連結程式庫 (DLL) 是程式庫中指定`Lib`子句`Declare`陳述式。 此錯誤的可能原因包括：  
  
-   檔案不是可執行檔的 DLL。  
  
-   檔案不是 Microsoft Windows DLL。  
  
-   DLL 會參考不存在的另一個 DLL。  
  
-   DLL 或參考的 DLL 不在路徑中指定的目錄。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   如果是檔案的原始程式文字檔案，因此不 DLL 可執行檔，它必須單獨編譯及連結至 DLL 可執行檔格式。  
  
-   如果檔案不是 Microsoft Windows DLL，取得對等的 Microsoft Windows。  
  
-   如果 DLL 參考不存在的另一個 DLL 時，取得參考的 DLL，並提供它。  
  
-   如果 DLL 或參考的 DLL 不是路徑所指定的目錄中，請將 DLL 移至參考的目錄。  
  
## <a name="see-also"></a>另請參閱

- [Declare 陳述式](../../../visual-basic/language-reference/statements/declare-statement.md)
