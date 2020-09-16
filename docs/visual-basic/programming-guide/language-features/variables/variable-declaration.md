---
title: 變數宣告
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], declaring
- member variables [Visual Basic], declarations
- Dim statement [Visual Basic], variable declaration
- declaring variables [Visual Basic]
- variables [Visual Basic], scope
- variables [Visual Basic], data types
- data types [Visual Basic], variable declarations
- lifetime [Visual Basic], variables
- variables [Visual Basic], lifetime
- access levels [Visual Basic], variables
- scope [Visual Basic], declaration statements
- variables [Visual Basic], access level
- local variables [Visual Basic], declarations
- scope [Visual Basic], variables
ms.assetid: d8f10226-92b1-480f-9f53-df377b2d7e15
ms.openlocfilehash: e3e2b6173a36490328801afd7fe711f1a003e2ae
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557472"
---
# <a name="variable-declaration-in-visual-basic"></a>Visual Basic 中的變數宣告
您可以宣告變數來指定其名稱和特性。 變數的宣告語句是 [Dim 語句](../../../language-reference/statements/dim-statement.md)。 其位置和內容會決定變數的特性。  
  
 如需變數命名規則和考慮，請參閱宣告的 [元素名稱](../declared-elements/declared-element-names.md)。  
  
## <a name="declaration-levels"></a>宣告層級  
  
### <a name="local-and-member-variables"></a>本機和成員變數  
 區域變數是在程式中宣告的 *變數* 。 *成員變數*是 Visual Basic 類型的成員;它是在模組層級、類別、結構或模組內宣告，而不是在該類別、結構或模組內部的任何程式內進行宣告。  
  
### <a name="shared-and-instance-variables"></a>共用和執行個體變數  
 在類別或結構中，成員變數的類別取決於它是否為共用。 如果它是以 [shared](../../../language-reference/modifiers/shared.md) 關鍵字宣告，它就是 *共用變數*，而且存在於類別或結構的所有實例之間共用的單一複本中。  
  
 否則，它是 *執行個體變數*，並且會為類別或結構的每個實例建立個別的複本。 執行個體變數的指定複本只適用于建立該實例之類別或結構的實例。 它獨立于類別或結構的任何其他實例中的執行個體變數複本。  
  
## <a name="declaring-data-type"></a>宣告資料類型  
 宣告語句中的 [As](../../../language-reference/statements/as-clause.md) 子句可讓您定義您所宣告之變數的資料類型或物件類型。 您可以為變數指定下列任何一種類型：  
  
- 基本資料類型，例如 `Boolean` 、 `Long` 或 `Decimal`  
  
- 複合資料型別，例如陣列或結構  
  
- 在您的應用程式或其他應用程式中定義的物件類型或類別  
  
- .NET Framework 類別，例如 <xref:System.Windows.Forms.Label> 或 <xref:System.Windows.Forms.TextBox>  
  
- 介面類別型，例如 <xref:System.IComparable> 或 <xref:System.IDisposable>  
  
 您可以在一個語句中宣告數個變數，而不需要重複資料類型。 在下列語句中，變數 `i` 、和 `j` 會宣告 `k` 為型別 `Integer` ，以及 `l` `m` as、and `Long` `x` 和 `y` as `Single` ：  
  
```vb  
Dim i, j, k As Integer  
' All three variables in the preceding statement are declared as Integer.  
Dim l, m As Long, x, y As Single  
' In the preceding statement, l and m are Long, x and y are Single.  
```  
  
 如需資料類型的詳細資訊，請參閱 [資料類型](../data-types/index.md)。 如需物件的詳細資訊，請參閱 [物件和類別](../objects-and-classes/index.md) 以及 [使用元件](/previous-versions/visualstudio/visual-studio-2013/0ffkdtkf(v=vs.120))進行程式設計。  
  
## <a name="local-type-inference"></a>區域類型推斷  
 *型別推斷* 用來判斷不使用子句宣告的區域變數資料類型 `As` 。 編譯器會從初始化運算式的類型推斷變數的類型。 這可讓您宣告變數，而不需要明確地指出類型。 在下列範例中， `num1` 和 `num2` 都是強型別為整數。  
  
 [!code-vb[VbVbalrTypeInference#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#1)]  
  
 如果您想要使用區欄位型別推斷， `Option Infer` 必須將設定為 `On` 。 如需詳細資訊，請參閱[區域型別推斷](local-type-inference.md)和 [Option Infer 陳述式](../../../language-reference/statements/option-infer-statement.md)。  
  
## <a name="characteristics-of-declared-variables"></a>宣告變數的特性  
 變數的 *存留* 期是可供使用的時間週期。 一般情況下，只要宣告 (的專案（如程式或類別）) 繼續存在，變數就會存在。 如果變數不需要在其包含元素的存留期之外繼續存在，您就不需要在宣告中執行任何特殊動作。 如果變數需要繼續比其包含元素更長的時間，您可以 `Static` `Shared` 在其語句中包含或關鍵字 `Dim` 。 如需詳細資訊，請參閱 [Visual Basic 中的存留期](../declared-elements/lifetime.md)。  
  
 變數的 *範圍* 是一組可以參考的程式碼，但不符合其名稱。 變數的範圍取決於其宣告位置。 位於指定區域中的程式碼可以使用在該區域中定義的變數，而不需限定其名稱。 如需詳細資訊，請參閱 [Scope in Visual Basic](../declared-elements/scope.md)。  
  
 變數的 *存取層級* 是具有存取權的程式碼範圍。 這取決於存取修飾詞 (例如您在語句中使用的 [公用](../../../language-reference/modifiers/public.md) 或 [私](../../../language-reference/modifiers/private.md) 用) `Dim` 。 如需詳細資訊，請參閱 [Visual Basic 中的存取層級](../declared-elements/access-levels.md)。  
  
## <a name="see-also"></a>另請參閱

- [如何：建立新的變數](how-to-create-a-new-variable.md)
- [如何：移入和移出變數資料](how-to-move-data-into-and-out-of-a-variable.md)
- [Data types (資料類型)](../../../language-reference/data-types/index.md)
- [保護](../../../language-reference/modifiers/protected.md)
- [Friend](../../../language-reference/modifiers/friend.md)
- [靜態](../../../language-reference/modifiers/static.md)
- [宣告項目特性](../declared-elements/declared-element-characteristics.md)
- [區域型別推斷](local-type-inference.md)
- [Option Infer 陳述式](../../../language-reference/statements/option-infer-statement.md)
