---
title: Ansi
ms.date: 07/20/2015
f1_keywords:
- vb.Ansi
helpviewer_keywords:
- Declare statement [Visual Basic], marshaling strings [Visual Basic]
- ANSI, Visual Basic
- ANSI
ms.assetid: 4f1fa6ff-5557-41ab-b6da-90baf4c15917
ms.openlocfilehash: 8dfd830e4c7ed97c8813da4ad310ee59b26f44f8
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90868805"
---
# <a name="ansi-visual-basic"></a>Ansi (Visual Basic)

指定 Visual Basic 應將所有字串封送處理成美國國家標準局 (ANSI) 值，而不論所宣告的外部程式名稱為何。  
  
 當您呼叫在專案之外定義的程式時，Visual Basic 編譯器無法存取正確呼叫程式所需的資訊。 這項資訊包括程式所在位置、識別方式、其呼叫順序和傳回型別，以及它所使用的字串字元集。 [Declare 語句](../statements/declare-statement.md)會建立外部程式的參考，並提供必要的資訊。  
  
 `charsetmodifier`語句中的部分會在 `Declare` 呼叫外部程式期間提供封送處理字串的字元集資訊。 它也會影響 Visual Basic 在外部檔案中搜尋外部程式名稱的方式。 修飾詞會 `Ansi` 指定 Visual Basic 應將所有字串封送處理成 ANSI 值，而且不應該在搜尋過程中修改程式的名稱。  
  
 如果未指定任何字元集修飾詞， `Ansi` 就是預設值。  
  
## <a name="remarks"></a>備註  

 `Ansi`修飾詞可用於此內容中：  
  
 [Declare Statement](../statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a>智慧型裝置開發人員注意事項  

 不支援這個關鍵字。  
  
## <a name="see-also"></a>另請參閱

- [Auto](auto.md)
- [Unicode](unicode.md)
- [關鍵字](../keywords/index.md)
