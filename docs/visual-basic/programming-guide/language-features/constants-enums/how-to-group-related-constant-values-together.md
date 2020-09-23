---
title: 如何：將關聯的常數值群組在一起
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], constants
- constants [Visual Basic], grouping together
ms.assetid: 09d61da5-c940-4126-a79f-ba93c36653dc
ms.openlocfilehash: 0f694aee722e8ce31f663ec9fe52a09a2eb2a958
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058725"
---
# <a name="how-to-group-related-constant-values-together-visual-basic"></a>如何：將關聯的常數值群組在一起 (Visual Basic)

列舉是將相關常數群組在一起的最佳方式。 您可以使用 `Enum` 類別或模組之宣告區段中的語句來建立列舉。 如需詳細資訊，請參閱 [如何：宣告列舉](how-to-declare-enumerations.md)。  
  
### <a name="to-group-related-constant-values"></a>若要將相關常數值分組  
  
1. 撰寫包含程式碼存取層級、 `Enum` 關鍵字和有效名稱的宣告。 這個範例會建立 `Private` 列舉型別 `temperatureValues` 。  
  
     [!code-vb[VbEnumsTask#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#21)]  
  
2. 定義列舉中的常數。 這個範例會建立 `Public` 列舉 `temperatureValues` 並指派其值。  
  
     [!code-vb[VbEnumsTask#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#1)]  
  
## <a name="see-also"></a>另請參閱

- [列舉和名稱限定性條件](enumerations-and-name-qualification.md)
- [如何：參考列舉類型成員](how-to-refer-to-an-enumeration-member.md)
- [何時使用列舉類型](when-to-use-an-enumeration.md)
- [常數的概觀](constants-overview.md)
- [常數和常值資料類型](constant-and-literal-data-types.md)
- [常數和列舉](../../../language-reference/constants-and-enumerations.md)
