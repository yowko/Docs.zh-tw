---
title: 無法參考至 '<name>'，因為它是類別 '<name>' 的實值類型欄位 '<classname>' 的成員，它把 'System.MarshalByRefObject' 當做基底類別
ms.date: 07/20/2015
f1_keywords:
- vbc30310
- bc30310
helpviewer_keywords:
- BC30310
ms.assetid: 2aeb8872-7c87-4f01-98ef-9714ba3eebbe
ms.openlocfilehash: 78b0a3131b6e77ed257f200523ecebd4dfce3691
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59316540"
---
# <a name="cannot-refer-to-name-because-it-is-a-member-of-the-value-typed-field-name-of-class-classname-which-has-systemmarshalbyrefobject-as-a-base-class"></a>無法參考 '\<名稱 >' 因為它是實值類型欄位的成員'\<名稱 >' 的類別\<類別名稱 >' 'system.marshalbyrefobject' 當做基底類別
`System.MarshalByRefObject`類別可讓您跨應用程式定義域界限支援遠端物件的存取權的應用程式。 類型必須繼承自`MarshalByRejectObject`類別，在跨應用程式定義域界限使用的型別。 因為物件的成員不是他們所建立的應用程式定義域外使用，必須不會複製物件的狀態。  
  
 **錯誤 ID:** BC30310  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 請檢查以確定所參考的成員都是有效的參考。  
  
2. 明確限定的成員`Me`關鍵字。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.MarshalByRefObject>
- [Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)
