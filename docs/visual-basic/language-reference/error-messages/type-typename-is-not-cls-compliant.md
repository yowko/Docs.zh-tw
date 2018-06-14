---
title: 型別&lt;typename&gt;不符合 CLS 標準
ms.date: 07/20/2015
f1_keywords:
- bc40041
- vbc40041
helpviewer_keywords:
- BC40041
ms.assetid: 634132c2-5646-44aa-98c6-f773e2e63882
ms.openlocfilehash: 9911b4fe7b88996f17cb5e9eec7d4a5f2c254b76
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33594604"
---
# <a name="type-lttypenamegt-is-not-cls-compliant"></a>型別&lt;typename&gt;不符合 CLS 標準
具有不符合 CLS 標準的資料類型來宣告變數、 屬性或函式傳回。  
  
 若要符合應用程式[語言獨立性以及與語言無關的元件](../../../standard/language-independence-and-language-independent-components.md)（cls） 標準，它必須使用只有符合 CLS 標準的類型。  
  
 下列 Visual Basic 資料類型不符合 CLS 標準：  
  
-   [SByte 資料類型](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [UInteger 資料類型](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [ULong 資料類型](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [UShort 資料類型](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 **錯誤 ID:** BC40041  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   如果您的應用程式必須符合 CLS 標準，變更的資料類型的這個項目為最接近符合 CLS 標準的類型。 例如，如果您不需要 2,147,483,647 以上的值範圍，而且不使用 `UInteger` ，則可能可以使用 `Integer` 。 如果您需要擴充範圍，則可以將 `UInteger` 取代為 `Long`。  
  
-   如果您的應用程式不需要符合 CLS 標準，您不需要變更任何項目。 您應該注意不相容的問題，不過。