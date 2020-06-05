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
ms.openlocfilehash: b9bdeed55788252c71b8fb1c995c140cbfdf60eb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84373124"
---
# <a name="auto-visual-basic"></a>Auto (Visual Basic)
指定 Visual Basic 應根據所宣告外部程式的外部名稱，依據 .NET Framework 規則封送處理字串。  
  
 當您呼叫在專案外部定義的程式時，Visual Basic 編譯器無法存取正確呼叫程式所需的資訊。 此資訊包括程式所在位置、識別方式、其呼叫順序和傳回類型，以及它所使用的字串字元集。 [Declare 語句](../statements/declare-statement.md)會建立外部程式的參考，並提供此必要資訊。  
  
 `charsetmodifier`語句中的部分會 `Declare` 提供字元集資訊，以便在呼叫外部程式期間封送處理字串。 它也會影響 Visual Basic 在外部檔案中搜尋外部程式名稱的方式。 `Auto`修飾詞會指定 Visual Basic 應該根據 .NET Framework 規則封送處理字串，而且應該判斷執行時間平臺的基底字元集，而且如果初始搜尋失敗，可能會修改外部程式名稱。 如需詳細資訊，請參閱[Declare 語句](../statements/declare-statement.md)中的「字元集」。  
  
 如果未指定任何字元集修飾詞， `Ansi` 則為預設值。  
  
## <a name="remarks"></a>備註  
 `Auto`修飾詞可以在此內容中使用：  
  
 [Declare Statement](../statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a>智慧型裝置開發人員注意事項  
 不支援這個關鍵字。  
  
## <a name="see-also"></a>另請參閱

- [Ansi](ansi.md)
- [消除](unicode.md)
- [關鍵字](../keywords/index.md)
