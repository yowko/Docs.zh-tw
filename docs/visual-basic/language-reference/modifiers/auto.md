---
title: 自動
ms.date: 07/20/2015
f1_keywords:
- vb.Auto
helpviewer_keywords:
- Auto keyword [Visual Basic], external references
- Declare statement [Visual Basic], marshaling strings
- Auto keyword [Visual Basic]
- Auto keyword [Visual Basic], marshaling strings
ms.assetid: bf79ba95-a62c-48a5-916f-0ac7a52c13ec
ms.openlocfilehash: 799a7320b701384dc5f4b4b46fef8544f6b15b02
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875519"
---
# <a name="auto-visual-basic"></a>Auto (Visual Basic)

指定 Visual Basic 應根據所宣告外部程式的外部名稱，根據 .NET Framework 規則來封送處理字串。  
  
 當您呼叫在專案之外定義的程式時，Visual Basic 編譯器無法存取正確呼叫程式所需的資訊。 這項資訊包括程式所在位置、識別方式、其呼叫順序和傳回型別，以及它所使用的字串字元集。 [Declare 語句](../statements/declare-statement.md)會建立外部程式的參考，並提供必要的資訊。  
  
 `charsetmodifier`語句中的部分會在 `Declare` 呼叫外部程式期間提供封送處理字串的字元集資訊。 它也會影響 Visual Basic 在外部檔案中搜尋外部程式名稱的方式。 修飾詞會 `Auto` 指定 Visual Basic 應根據 .NET Framework 的規則來封送處理字串，而且它應該判斷執行時間平臺的基底字元集，而且如果初始搜尋失敗，可能會修改外部程式名稱。 如需詳細資訊，請參閱 [Declare 語句](../statements/declare-statement.md)中的「字元集」。  
  
 如果未指定任何字元集修飾詞， `Ansi` 就是預設值。  
  
## <a name="remarks"></a>備註  

 `Auto`修飾詞可用於此內容中：  
  
 [Declare Statement](../statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a>智慧型裝置開發人員注意事項  

 不支援這個關鍵字。  
  
## <a name="see-also"></a>另請參閱

- [Ansi](ansi.md)
- [Unicode](unicode.md)
- [關鍵字](../keywords/index.md)
