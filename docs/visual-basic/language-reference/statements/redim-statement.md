---
title: ReDim 陳述式 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ReDim
- vb.Preserve
helpviewer_keywords:
- fixed-length strings [Visual Basic], declaring
- ReDim statement [Visual Basic], syntax
- dynamic arrays [Visual Basic], ReDim statement
- arrays [Visual Basic], reallocating
- arrays [Visual Basic], reinitializing
- arrays [Visual Basic], dimensions
- scalars, and arrays
- scalars
- declarations [Visual Basic], dynamic arrays
- variables [Visual Basic], scalar
- ReDim statement [Visual Basic]
- data types [Visual Basic], assigning
- As keyword [Visual Basic], in ReDim statement
- To keyword [Visual Basic], ReDim statement
- arrays [Visual Basic], declaring
- Preserve keyword [Visual Basic], ReDim statement
- storage [Visual Basic], allocating
- arrays [Visual Basic], and scalars
- declaration statements [Visual Basic]
- scalar variables [Visual Basic]
ms.assetid: ad1c5e07-dcd7-4ae1-a79e-ad3f2dcc2083
ms.openlocfilehash: 9536ea8a6274e0b4a2589caf5aefa271a3567d32
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33605390"
---
# <a name="redim-statement-visual-basic"></a>ReDim 陳述式 (Visual Basic)
重新配置陣列變數的儲存空間。  
  
## <a name="syntax"></a>語法  
  
```  
ReDim [ Preserve ] name(boundlist) [ ,  name(boundlist) [, ... ] ]  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|----------|----------------|  
|`Preserve`|選擇性。 僅變更最後維度的大小時，用來保留現有陣列資料的修飾詞。|  
|`name`|必要。 陣列變數的名稱。 請參閱[宣告項目名稱](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。|  
|`boundlist`|必要。 重新定義之陣列各維度的界限清單。|  
  
## <a name="remarks"></a>備註  
 您可以使用 `ReDim` 陳述式變更已宣告陣列的一或多個維度的大小。 如果您有大型的陣列，而且不再需要其中某些項目，`ReDim` 可以減少陣列大小，釋出記憶體。 另一方面，如果陣列需要更多項目，`ReDim` 可以加入項目。  
  
 `ReDim` 陳述式僅供陣列使用。 對純量 (僅含單一值的變數)、集合或結構無效。 請注意，如果您宣告變數為類型 `Array`，則 `ReDim` 陳述式就沒有足夠的類型資訊建立新的陣列。  
  
 `ReDim` 只能在程序層級使用。 因此，變數的宣告內容必須是程序，不能是原始程式檔、命名空間、介面、類別、結構、模組或區塊。 如需詳細資訊，請參閱[宣告內容和預設存取層級](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。  
  
## <a name="rules"></a>規則  
  
-   **多個變數。** 您可以調整相同宣告陳述式中數個陣列變數的大小，並為每個變數指定 `name` 和 `boundlist` 組件。 以逗號分隔多個變數。  
  
-   **陣列界限。** `boundlist` 中的每個項目都可以指定該維度的上下限。 下限一律為 0 (零)。 上限是該維度可能的最高索引值，不是維度長度 (上限加 1)。 每個維度的索引從 0 到上限值不等。  
  
     `boundlist` 中的維度數目必須符合陣列的原始維度 (陣序) 數目。  
  
-   **資料型別。** `ReDim` 陳述式不能變更其項目陣列變數的資料類型。  
  
-   **初始化。** `ReDim` 陳述式不能提供陣列項目的新初始化值。  
  
-   **陣序。** `ReDim` 陳述式不能變更陣列的陣序 (維度數目)。  
  
-   **以 Preserve 調整大小。** 如果使用 `Preserve`，您也可以只調整陣列的最後一個維度。 至於其他每個維度，您必須指定現有陣列的界限。  
  
     例如，如果您的陣列只有一個維度，您可以調整該維度的大小，但仍保留陣列的所有內容，因為您變更的只有最後一個維度。 不過，如果您的陣列有兩個或以上的維度，如果使用 `Preserve`，就只能變更最後一個維度的大小。  
  
-   **屬性。** `ReDim` 可以用在保存值陣列的屬性。  
  
## <a name="behavior"></a>行為  
  
-   **陣列取代。** `ReDim` 釋放現有的陣列，並使用相同的陣序建立新的陣列。 新的陣列會取代陣列變數中已釋放的陣列。  
  
-   **不使用 Preserve 的初始化。** 如果不指定 `Preserve`，`ReDim` 會使用其資料類型的預設值，初始化新的陣列項目。  
  
-   **使用 Preserve 的初始化。** 如果指定 `Preserve`，Visual Basic 會將現有陣列的項目複製到新陣列。  
  
## <a name="example"></a>範例  
 下列範例會增加動態陣列最後一個維度的大小，但不會遺失陣列現有的任何資料，再以遺失部分資料的方式減少大小。 最後，大小減少回其原始值，並重新初始化所有陣列項目。  
  
 [!code-vb[VbVbalrStatements#52](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/redim-statement_1.vb)]  
  
 `Dim` 陳述式會建立三維的新陣列。 每個維度都宣告界限為 10，所以每個維度的陣列索引範圍是 0 到 10。 在下列的討論中，三維稱為圖層、列和欄。  
  
 第一個 `ReDim` 建立的新陣列，取代了變數 `intArray` 中現有的陣列。 `ReDim` 將現有陣列的所有項目全都複製到新的陣列。 它也在每個圖層每一列的結尾加入 10 多個欄，並初始化這些新欄中的項目為 0 (`Integer` 的預設值，這是陣列的項目類型)。  
  
 第二個 `ReDim` 建立另一個新的陣列，並複製所有符合的項目。 不過，每個圖層每一列的結尾都會遺失五欄。 如果不再使用這些欄就沒有問題。 減少大型陣列的大小可以釋出不再需要的記憶體。  
  
 第三個 `ReDim` 建立另一個新的陣列，並從每個圖層的每一列結尾移除另外五欄。 這次不複製任何現有的項目。 這個陳述式會將陣列還原成原始大小。 因為陳述式不包含 `Preserve` 修飾詞，所以所有的陣列項目都設為原始預設值。  
  
 如需其他範例，請參閱[陣列](../../../visual-basic/programming-guide/language-features/arrays/index.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.IndexOutOfRangeException>  
 [Const 陳述式](../../../visual-basic/language-reference/statements/const-statement.md)  
 [Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [Erase 陳述式](../../../visual-basic/language-reference/statements/erase-statement.md)  
 [Nothing](../../../visual-basic/language-reference/nothing.md)  
 [陣列](../../../visual-basic/programming-guide/language-features/arrays/index.md)
