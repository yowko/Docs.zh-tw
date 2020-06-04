---
title: Delegate 陳述式
ms.date: 07/20/2015
f1_keywords:
- vb.Delegate
helpviewer_keywords:
- delegate keyword [Visual Basic]
- Delegate statement [Visual Basic]
ms.assetid: f799c518-0817-40cc-ad0b-4da846fdba57
ms.openlocfilehash: 8dec28620b0409f05007b2c0b1c1fd4494c2d7c8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404754"
---
# <a name="delegate-statement"></a>Delegate 陳述式
用來宣告委派。 「委派」（delegate）是參考型別，它會參考 `Shared` 型別的方法或物件的實例方法。 任何具有相符參數和傳回類型的程式都可以用來建立此委派類別的實例。 稍後可以透過委派實例叫用此程式。  
  
## <a name="syntax"></a>語法  
  
```vb  
[ <attrlist> ] [ accessmodifier ] _  
[ Shadows ] Delegate [ Sub | Function ] name [( Of typeparamlist )] [([ parameterlist ])] [ As type ]  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`attrlist`|選擇性。 適用于此委派的屬性清單。 以逗號分隔多個屬性。 您必須將[屬性清單](attribute-list.md)放在角括弧（" `<` " 和 " `>` "）中。|  
|`accessmodifier`|選擇性。 指定哪些程式碼可以存取委派。 可以是下列其中一項：<br /><br /> - [公用](../modifiers/public.md)。 任何可以存取宣告委派之專案的程式碼都可以存取它。<br />-   [受保護](../modifiers/protected.md)。 只有委派類別或衍生類別內的程式碼可以存取它。<br />-   [Friend](../modifiers/friend.md)。 只有相同元件中的程式碼可以存取委派。<br />- [私](../modifiers/private.md)用。 只有宣告委派之元素內的程式碼才能存取它。<br /><br /> - [受保護的 Friend](../modifiers/protected-friend.md)只有委派的類別、衍生類別或相同元件中的程式碼可以存取委派。 <br />- [私用保護](../modifiers/private-protected.md)只有委派類別或相同元件中的衍生類別內的程式碼可以存取委派。 |  
|`Shadows`|選擇性。 表示這個委派會重新宣告並隱藏基類中名稱相同的程式設計項目，或一組多載元素。 您可以使用任何其他類型遮蔽任何一種已宣告的項目。<br /><br /> 無法從遮蔽項目的衍生類別內使用遮蔽的項目，除了從無法存取遮蔽項目的位置以外。 例如，如果專案 `Private` 遮蔽基類元素，則沒有許可權存取專案的程式碼會改為存取 `Private` 基類元素。|  
|`Sub`|選擇性，但 `Sub` 或 `Function` 必須出現。 將此程式宣告為不 `Sub` 會傳回值的委派程式。|  
|`Function`|選擇性，但 `Sub` 或 `Function` 必須出現。 將此程式宣告為傳回 `Function` 值的委派程式。|  
|`name`|必要。 委派類型的名稱;遵循標準變數命名慣例。|  
|`typeparamlist`|選擇性。 此委派的型別參數清單。 多個類型參數會以逗號分隔。 您可以選擇性地使用和泛型修飾詞，將每個類型參數宣告為 variant `In` `Out` 。 您必須將[類型清單](type-list.md)括在括弧中，並使用關鍵字加以引進 `Of` 。|  
|`parameterlist`|選擇性。 呼叫時傳遞至程式的參數清單。 您必須將[參數清單](parameter-list.md)括在括弧中。|  
|`type`|如果您指定程式，則為必要 `Function` 。 傳回值的資料類型。|  
  
## <a name="remarks"></a>備註  
 `Delegate`語句會定義委派類別的參數和傳回類型。 任何具有相符參數和傳回類型的程式都可以用來建立此委派類別的實例。 藉由呼叫委派的方法，稍後可以透過委派實例叫用此程式 `Invoke` 。  
  
 委派可以在命名空間、模組、類別或結構層級宣告，但不能在程式內宣告。  
  
 每個委派類別會為傳遞的建構函式定義物件方法的規格。 對委派建構函式的引數必須是對方法的參考或 lambda 運算式。  
  
 若要指定對方法的參考，請使用下列語法：  
  
 `AddressOf` [`expression`.]`methodname`  
  
 `expression` 的編譯時期型別必須是類別或介面的名稱，而該類別或介面包含其簽章符合委派類別簽章的特定名稱方法。 `methodname` 可以是共用的方法或執行個體方法。 `methodname` 不是選擇性的，即使您為類別的預設方法建立了委派也一樣。  
  
 若要指定 lambda 運算式，請使用下列語法：  
  
 `Function` ([`parm` As `type`, `parm2` As `type2`, ...]) `expression`  
  
 函式的簽章必須符合委派型別的簽章。 如需 lambda 運算式的詳細資訊，請參閱[Lambda 運算式](../../programming-guide/language-features/procedures/lambda-expressions.md)。  
  
 如需委派的詳細資訊，請參閱[委派](../../programming-guide/language-features/delegates/index.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用 `Delegate` 語句來宣告委派，以對兩個數字進行操作並傳回數位。 `DelegateTest`方法會採用此類型的委派實例，並使用它來運算元字配對。  
  
 [!code-vb[VbVbalrDelegates#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#14)]  
  
## <a name="see-also"></a>另請參閱

- [AddressOf 運算子](../operators/addressof-operator.md)
- [的](of-clause.md)
- [委派](../../programming-guide/language-features/delegates/index.md)
- [作法：使用泛型類別](../../programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [Generic Types in Visual Basic](../../programming-guide/language-features/data-types/generic-types.md)
- [共變數和反變數](../../programming-guide/concepts/covariance-contravariance/index.md)
- [位於](../modifiers/in-generic-modifier.md)
- [脫銷](../modifiers/out-generic-modifier.md)
