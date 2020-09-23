---
title: 如何：宣告列舉
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], enumerations
- enumerations [Visual Basic], declaring
- declaring enumerations [Visual Basic]
ms.assetid: db4ca1c3-f429-4c81-ae81-29e0157b29fd
ms.openlocfilehash: 752b425ba32efe41a1ab1aa75de20039d36f5e50
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058894"
---
# <a name="how-to-declare-enumerations-visual-basic"></a>如何：宣告列舉 (Visual Basic)

您可以使用 `Enum` 類別或模組之宣告區段中的語句來建立列舉。 您無法在方法內宣告列舉。 若要指定適當的存取層級，請使用 `Private` 、、 `Protected` `Friend` 或 `Public` 。  
  
 `Enum`型別具有名稱、基礎類型和一組欄位，每個都代表一個常數。 名稱必須是有效的 Visual Basic .NET 限定詞。 基礎類型必須是其中一個整數類型： `Byte` 、 `Short` `Long` 或 `Integer` 。 `Integer` 是預設值。 列舉一律為強型別，而且無法與整數類型交換。  
  
 列舉不能有浮點值。 如果列舉型別指派了浮點值，就會 `Option Strict On` 產生編譯器錯誤。 如果 `Option Strict` 為 `Off` ，則值會自動轉換成 `Enum` 類型。  
  
 如需名稱的相關資訊，以及如何使用 `Imports` 語句來限定名稱限定性，請參閱列舉 [和名稱限定](enumerations-and-name-qualification.md)性。  
  
### <a name="to-declare-an-enumeration"></a>宣告列舉  
  
1. 撰寫包含程式碼存取層級、 `Enum` 關鍵字和有效名稱的宣告，如下列範例所示，每個宣告都是不同的 `Enum` 。  
  
     [!code-vb[VbEnumsTask#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#3)]  
  
2. 定義列舉中的常數。 根據預設，列舉中的第一個常數會初始化為 `0` ，而且後續的常數會初始化為比上一個常數還多的值。 例如，下列列舉會包含名為的常數、以值命名的常數 `Days` `Sunday` `0` `Monday` `1` 、以的值命名的常數， `Tuesday` `2` 依此類推。  
  
     [!code-vb[VbEnumsTask#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#4)]  
  
3. 您可以使用指派語句，將值明確指派給列舉中的常數。 您可以指派包含負數的任何整數值。 例如，您可能想要值小於零的常數來表示錯誤狀況。 在下列列舉中， `Invalid` 會明確地將值指派給常數 `–1` ，並將 `Sunday` 值指派給常數 `0` 。 因為它是列舉中的第一個常數，所以 `Saturday` 也會初始化為值 `0` 。 的值 `Monday` `1` (一個以上的值 `Sunday`) ; 的值 `Tuesday` 為 `2` ，依此類推。  
  
     [!code-vb[VbEnumsTask#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#5)]  
  
### <a name="to-declare-an-enumeration-as-an-explicit-type"></a>將列舉宣告為明確類型  
  
- 使用子句來指定列舉的型別 `As` ，如下列範例所示。  
  
     [!code-vb[VbEnumsTask#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#6)]  
  
## <a name="see-also"></a>另請參閱

- [列舉和名稱限定性條件](enumerations-and-name-qualification.md)
- [如何：參考列舉類型成員](how-to-refer-to-an-enumeration-member.md)
- [如何：在 Visual Basic 中逐一查看列舉類型](how-to-iterate-through-an-enumeration.md)
- [如何：決定與列舉值相關聯的字串](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [何時使用列舉類型](when-to-use-an-enumeration.md)
- [常數的概觀](constants-overview.md)
- [常數和常值資料類型](constant-and-literal-data-types.md)
- [常數和列舉](../../../language-reference/constants-and-enumerations.md)
