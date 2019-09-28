---
title: GetType 運算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.GetType
helpviewer_keywords:
- GetType operator [Visual Basic]
- GetType keyword [Visual Basic]
ms.assetid: 4f733297-2503-4607-850c-15eba65fff90
ms.openlocfilehash: 2e3e05973f2ef72fef5e429bc98cc58b4b21f2c2
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592157"
---
# <a name="gettype-operator-visual-basic"></a>GetType 運算子 (Visual Basic)
傳回指定之類型的 <xref:System.Type> 物件。 @No__t-0 物件提供類型的相關資訊，例如其屬性、方法和事件。  
  
## <a name="syntax"></a>語法  
  
```vb  
GetType(typename)  
```  
  
## <a name="parameters"></a>參數  
  
|參數|描述|  
|---|---|  
|`typename`|您想要其資訊的類型名稱。|  
  
## <a name="remarks"></a>備註  
 @No__t-0 運算子會針對指定的 `typename` 傳回 <xref:System.Type> 物件。 您可以在 `typename` 中傳遞任何已定義類型的名稱。 其中包括下列項目：  
  
- 任何 Visual Basic 資料類型，例如 `Boolean` 或 `Date`。  
  
- 任何 .NET Framework 類別、結構、模組或介面，例如 <xref:System.ArgumentException?displayProperty=nameWithType> 或 <xref:System.Double?displayProperty=nameWithType>。  
  
- 您的應用程式所定義的任何類別、結構、模組或介面。  
  
- 您的應用程式所定義的任何陣列。  
  
- 您的應用程式所定義的任何委派。  
  
- Visual Basic、.NET Framework 或您的應用程式所定義的任何列舉。  
  
 如果您想要取得物件變數的類型物件，請使用 <xref:System.Type.GetType%2A?displayProperty=nameWithType> 方法。  
  
 在下列情況下，`GetType` 運算子可能會很有用：  
  
- 您必須在執行時間存取類型的中繼資料。 @No__t 0 物件提供中繼資料，例如類型成員和部署資訊。 例如，您需要此來反映元件。 如需詳細資訊，請參閱<xref:System.Reflection?displayProperty=nameWithType>。  
  
- 您想要比較兩個物件參考，以查看它們是否參考相同類型的實例。 如果有，`GetType` 會傳回相同 <xref:System.Type> 物件的參考。  
  
## <a name="example"></a>範例  
 下列範例顯示使用中的 `GetType` 運算子。  
  
 [!code-vb[VbVbalrOperators#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#26)]  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [運算子和運算式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
