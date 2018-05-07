---
title: GetType 運算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.GetType
helpviewer_keywords:
- GetType operator [Visual Basic]
- GetType keyword [Visual Basic]
ms.assetid: 4f733297-2503-4607-850c-15eba65fff90
ms.openlocfilehash: 581f576222eb149aede841a5da7a0e5f38c77b58
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="gettype-operator-visual-basic"></a>GetType 運算子 (Visual Basic)
傳回<xref:System.Type>指定類型的物件。 <xref:System.Type>物件提供類型，例如其屬性、 方法和事件的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```  
GetType(typename)  
```  
  
#### <a name="parameters"></a>參數  
  
|參數|描述|  
|---|---|  
|`typename`|您想要的資訊類型的名稱。|  
  
## <a name="remarks"></a>備註  
 `GetType`運算子會傳回<xref:System.Type>物件指定`typename`。 您可以傳遞任何已定義型別的名稱`typename`。 其中包括下列項目：  
  
-   Visual Basic 中的任何資料類型，例如`Boolean`或`Date`。  
  
-   任何.NET Framework 類別、 結構、 模組或介面，例如<xref:System.ArgumentException?displayProperty=nameWithType>或<xref:System.Double?displayProperty=nameWithType>。  
  
-   任何類別、 結構、 模組或應用程式所定義的介面。  
  
-   應用程式所定義的任何陣列。  
  
-   任何應用程式所定義的委派。  
  
-   Visual Basic、.NET Framework 中或您的應用程式所定義的任何列舉類型。  
  
 如果您想要取得之物件變數的型別物件，使用<xref:System.Type.GetType%2A?displayProperty=nameWithType>方法。  
  
 `GetType`運算子只能在下列情況下很有用：  
  
-   您必須在執行階段存取類型的中繼資料。 <xref:System.Type>物件會提供中繼資料，例如型別成員和部署資訊。 您需要此，例如，以反映透過組件。 如需詳細資訊，請參閱<xref:System.Reflection?displayProperty=nameWithType>。  
  
-   您想要比較兩個物件參考，以查看它們是否參考相同類型的執行個體。 如果沒有的話，`GetType`傳回相同的參考<xref:System.Type>物件。  
  
## <a name="example"></a>範例  
 下列範例會顯示`GetType`中使用的運算子。  
  
 [!code-vb[VbVbalrOperators#26](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/gettype-operator_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [運算子和運算式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
