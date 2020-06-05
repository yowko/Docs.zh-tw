---
title: 類型 <typename> 不符合 CLS 標準
ms.date: 07/20/2015
f1_keywords:
- bc40041
- vbc40041
helpviewer_keywords:
- BC40041
ms.assetid: 634132c2-5646-44aa-98c6-f773e2e63882
ms.openlocfilehash: eacf5036ebc6fc31dfa0e8de39c4fb574c9072b3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84386954"
---
# <a name="type-typename-is-not-cls-compliant"></a>類型 \<typename> 不符合 CLS 標準
變數、屬性或函式傳回宣告的資料類型不符合 CLS 標準。  
  
 若要讓應用程式符合[語言獨立性和與語言無關的元件](../../../standard/language-independence-and-language-independent-components.md)（CLS）規範，它必須僅使用符合 CLS 標準的類型。  
  
 下列 Visual Basic 資料類型不符合 CLS 標準：  
  
- [SByte 資料類型](../data-types/sbyte-data-type.md)  
  
- [UInteger 資料類型](../data-types/uinteger-data-type.md)  
  
- [ULong 資料類型](../data-types/ulong-data-type.md)  
  
- [UShort 資料類型](../data-types/ushort-data-type.md)  
  
 **錯誤識別碼：** BC40041  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 如果您的應用程式必須符合 CLS 標準，請將這個元素的資料類型變更為最符合 CLS 標準的類型。 例如，如果您不需要 2,147,483,647 以上的值範圍，而且不使用 `UInteger` ，則可能可以使用 `Integer` 。 如果您需要擴充範圍，則可以將 `UInteger` 取代為 `Long`。  
  
- 如果您的應用程式不需要符合 CLS 標準，您就不需要變更任何專案。 不過，您應該知道它不相容。
