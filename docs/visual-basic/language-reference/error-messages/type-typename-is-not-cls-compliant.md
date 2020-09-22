---
title: 類型 <typename> 不符合 CLS 標準
ms.date: 07/20/2015
f1_keywords:
- bc40041
- vbc40041
helpviewer_keywords:
- BC40041
ms.assetid: 634132c2-5646-44aa-98c6-f773e2e63882
ms.openlocfilehash: 369516fb12b24981eaecfe467bf421dec279aa01
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875091"
---
# <a name="type-typename-is-not-cls-compliant"></a>類型 \<typename> 不符合 CLS 標準

變數、屬性或函式傳回所宣告的資料類型不符合 CLS 規範。  
  
 若要讓應用程式符合 [語言獨立性以及與語言無關的元件](../../../standard/language-independence-and-language-independent-components.md) (cls) ，它必須只使用符合 cls 標準的類型。  
  
 下列 Visual Basic 資料類型不符合 CLS 規範：  
  
- [SByte 資料類型](../data-types/sbyte-data-type.md)  
  
- [UInteger 資料類型](../data-types/uinteger-data-type.md)  
  
- [ULong 資料類型](../data-types/ulong-data-type.md)  
  
- [UShort 資料類型](../data-types/ushort-data-type.md)  
  
 **錯誤識別碼：** BC40041  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 如果您的應用程式必須符合 CLS 規範，請將這個元素的資料類型變更為最接近 CLS 標準的類型。 例如，如果您不需要 2,147,483,647 以上的值範圍，而且不使用 `UInteger` ，則可能可以使用 `Integer` 。 如果您需要擴充範圍，則可以將 `UInteger` 取代為 `Long`。  
  
- 如果您的應用程式不需要符合 CLS 標準，您就不需要變更任何變更。 不過，您應該知道它不符合規範。
