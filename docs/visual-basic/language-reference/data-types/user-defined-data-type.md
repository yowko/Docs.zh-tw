---
title: 使用者定義資料類型 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- UserDefined
- UDT
- vb.UDT
- User-Defined
- vb.UserDefined
- vb.User-Defined
helpviewer_keywords:
- user-defined data types [Visual Basic], Visual Basic
- user-defined types
- structures [Visual Basic], as user-defined data types
- user-defined types [Visual Basic], Visual Basic
- user-defined types [Visual Basic], structure declaration
- user-defined types [Visual Basic], structures in Visual Basic
- user-defined data types [Visual Basic], structure declaration
- data types [Visual Basic], assigning
- Structure statement [Visual Basic]
- data types [Visual Basic], user-defined
- user-defined data types [Visual Basic], structures in Visual Basic
- user-defined data types
- types [Visual Basic], user-defined
ms.assetid: be913dca-a364-4a51-96a1-549a1b390b0a
ms.openlocfilehash: 5fe12d18c7f403c1a50ed548a260ba39e83280eb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61746716"
---
# <a name="user-defined-data-type"></a>使用者定義資料類型
在您定義的格式保存資料。 `Structure`陳述式定義的格式。  
  
 舊版的 Visual Basic 支援使用者定義的型別 (UDT)。 目前的版本會擴展 UDT*結構*。 結構是一或多個串連*成員*的各種資料類型。 Visual Basic 會將結構視為單一單位，雖然您也可以個別地存取其成員。  
  
## <a name="remarks"></a>備註  
 定義和使用結構的資料類型，當您需要將各種資料型別結合成單一單位，或沒有任何基礎資料類型提供您的需求。  
  
 結構的資料類型的預設值是由每個成員的預設值的組合所組成。  
  
## <a name="declaration-format"></a>宣告格式  
 結構宣告的開頭[Structure 陳述式](../../../visual-basic/language-reference/statements/structure-statement.md)，並結束`End Structure`陳述式。 `Structure`陳述式提供結構，這也是結構定義資料類型的識別項的名稱。 其他部分的程式碼可以使用這個識別碼，來宣告變數、 參數和函式會傳回這個結構的資料類型的值。  
  
 宣告之間`Structure`和`End Structure`陳述式定義的結構成員。  
  
## <a name="member-access-levels"></a>成員存取層級  
 您必須使用每個成員的宣告[Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)或陳述式，指定存取層級，例如[公用](../../../visual-basic/language-reference/modifiers/public.md)， [Friend](../../../visual-basic/language-reference/modifiers/friend.md)，或[私用](../../../visual-basic/language-reference/modifiers/private.md). 如果您使用`Dim`陳述式中，為公用存取層級預設值。  
  
## <a name="programming-tips"></a>程式設計提示  
  
- **記憶體耗用量。** 如同所有的複合資料類型，您無法合併其成員的名義上的儲存體配置，安全地計算結構的總記憶體耗用量。 此外，您無法安全地假設在記憶體中的儲存體的順序是您宣告的順序相同。 如果您需要控制結構的儲存體配置，您可以申請<xref:System.Runtime.InteropServices.StructLayoutAttribute>屬性設定為`Structure`陳述式。  
  
- **Interop 考量。** 如果您要使用的不是針對.NET Framework 撰寫的元件，例如 Automation 或 COM 物件，請記住，在其他環境中的 使用者定義型別不相容於 Visual Basic 結構類型。  
  
- **擴展。** 沒有自動轉換至或從任何結構的資料型別。 您可以定義轉換運算子，在您使用結構[Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md)，而您可以宣告為每個轉換運算子`Widening`或`Narrowing`。  
  
- **類型字元。** 結構的資料類型會有任何常值類型字元或識別項類型字元。  
  
- **Framework 型別。** .NET Framework 中沒有任何對應的型別。 所有的結構會繼承自.NET Framework 類別<xref:System.ValueType?displayProperty=nameWithType>，但沒有個別的結構會對應至<xref:System.ValueType?displayProperty=nameWithType>。  
  
## <a name="example"></a>範例  
 下列範例說明結構宣告的外框。  
  
```  
[Public | Protected | Friend | Protected Friend | Private] Structure structname  
    {Dim | Public | Friend | Private} member1 As datatype1  
    ' ...  
    {Dim | Public | Friend | Private} memberN As datatypeN  
End Structure  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ValueType>
- <xref:System.Runtime.InteropServices.StructLayoutAttribute>
- [資料類型](../../../visual-basic/language-reference/data-types/index.md)
- [類型轉換函式](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [轉換摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Structure 陳述式](../../../visual-basic/language-reference/statements/structure-statement.md)
- [Widening](../../../visual-basic/language-reference/modifiers/widening.md)
- [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md)
- [結構](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [有效率地使用資料類型](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
