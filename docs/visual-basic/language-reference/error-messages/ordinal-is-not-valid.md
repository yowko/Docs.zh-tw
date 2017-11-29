---
title: "無效的序數"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID452
ms.assetid: 7459562b-cd4f-4590-95e0-6126ae3589a5
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d31d0fba19cc16004c0b56786af30603d0c509ea
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="ordinal-is-not-valid"></a>無效的序數
使用數字，而不是程序名稱，指示您動態連結程式庫 (DLL) 的呼叫使用`#num`語法。 此錯誤有下列可能原因：  
  
-   嘗試將轉換`#num`無法為序數的運算式。  
  
-   `#num`指定 DLL 中未指定任何函式。  
  
-   類型程式庫有無效的宣告導致無效的序數數字的內部使用。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  請確定運算式代表有效的數字，或呼叫程序的名稱。  
  
2.  請確定`#num`識別 DLL 中是有效的函數。  
  
3.  找出造成問題，註解的程式碼的程序呼叫。 寫入`Declare`程序，並回報問題類型程式庫的供應商的陳述式。  
  
## <a name="see-also"></a>另請參閱  
 [Declare 陳述式](../../../visual-basic/language-reference/statements/declare-statement.md)
