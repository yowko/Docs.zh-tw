---
title: GetType 運算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.GetType
helpviewer_keywords:
- GetType operator [Visual Basic]
- GetType keyword [Visual Basic]
ms.assetid: 4f733297-2503-4607-850c-15eba65fff90
ms.openlocfilehash: e3b4ee9a1bfcc2132d3e9e1239ff2c8f7158e513
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56966758"
---
# <a name="gettype-operator-visual-basic"></a>GetType 運算子 (Visual Basic)
傳回<xref:System.Type>指定之類型的物件。 <xref:System.Type>物件提供類型，例如其屬性、 方法和事件的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```  
GetType(typename)  
```  
  
#### <a name="parameters"></a>參數  
  
|參數|描述|  
|---|---|  
|`typename`|您想要的資訊類型的名稱。|  
  
## <a name="remarks"></a>備註  
 `GetType`運算子會傳回<xref:System.Type>所指定的物件`typename`。 您可以傳遞中任何已定義類型的名稱`typename`。 其中包括下列項目：  
  
-   Visual Basic 中的任何資料類型，例如`Boolean`或`Date`。  
  
-   任何.NET Framework 類別、 結構、 模組或介面，例如<xref:System.ArgumentException?displayProperty=nameWithType>或<xref:System.Double?displayProperty=nameWithType>。  
  
-   任何類別、 結構、 模組或應用程式所定義的介面。  
  
-   應用程式定義的任何陣列。  
  
-   應用程式定義的任何委派。  
  
-   Visual Basic、.NET Framework 中或您的應用程式所定義的任何列舉類型。  
  
 如果您想要取得的物件變數的型別物件，使用<xref:System.Type.GetType%2A?displayProperty=nameWithType>方法。  
  
 `GetType`運算子可用於下列情況：  
  
-   您必須在執行階段存取類型的中繼資料。 <xref:System.Type>物件會提供中繼資料，例如型別成員和部署資訊。 您需要，比方說，以反映的組件。 如需詳細資訊，請參閱<xref:System.Reflection?displayProperty=nameWithType>。  
  
-   您想要比較兩個物件參考，以查看它們是否參考相同類型的執行個體。 如果沒有的話，`GetType`會傳回相同的參考<xref:System.Type>物件。  
  
## <a name="example"></a>範例  
 下列範例會顯示`GetType`中使用的運算子。  
  
 [!code-vb[VbVbalrOperators#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#26)]  
  
## <a name="see-also"></a>另請參閱
- [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [運算子和運算式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
