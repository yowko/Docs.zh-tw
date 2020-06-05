---
title: 其他資料類型
ms.date: 07/20/2015
helpviewer_keywords:
- Object data type [Visual Basic], data types
- data types [Visual Basic], choosing
ms.assetid: 64c71a12-9057-4dbf-baca-7379c4aada69
ms.openlocfilehash: 0a08c0e7087c3efb0e5ffce51182defae45629ea
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393749"
---
# <a name="miscellaneous-data-types-visual-basic"></a>其他資料類型 (Visual Basic)
Visual Basic 提供幾個未導向數位或字元的資料類型。 相反地，它們會處理特定的資料，例如「是/否值」、「日期/時間值」和「物件位址」。  
  
 如需顯示 Visual Basic 資料類型並存比較的資料表，請參閱[資料類型](../../../language-reference/data-types/index.md)。  
  
## <a name="boolean-type"></a>布林值類型  
 [布林資料類型](../../../language-reference/data-types/boolean-data-type.md)是一種不帶正負號的值，會被視為 `True` 或 `False` 。 其資料寬度取決於執行平臺。 如果變數只能包含兩個狀態值（例如 true/false、yes/no 或 on/off），請將它宣告為 `Boolean` 。  
  
## <a name="date-type"></a>日期類型  
 [Date 資料類型](../../../language-reference/data-types/date-data-type.md)是同時保存日期和時間資訊的64位值。 每個增量代表西曆中第1年1月1日開始（12:00 AM）以來經過一段時間的100毫微秒。 如果變數可以包含日期值、時間值或兩者，請將它宣告為 `Date` 。  
  
## <a name="object-type"></a>物件類型  
 [Object 資料類型](../../../language-reference/data-types/object-data-type.md)是32位位址，指向應用程式或其他應用程式中的物件實例。 `Object`變數可以參考您的應用程式可辨識的任何物件，或是任何資料類型的資料。 這包括實*值*型別，例如 `Integer` 、和 `Boolean` 結構實例，以及*參考*型別，這些是從和等類別建立的物件實例 `String` ， <xref:System.Windows.Forms.Form> 以及陣列實例。  
  
 如果變數儲存的指標指向您在編譯時期不知道的類別實例，或如果它可以指向各種資料類型的資料，請將它宣告為 `Object` 。  
  
 資料類型的優點 `Object` 是您可以使用它來儲存任何資料類型的資料。 缺點是您會產生額外的作業，以執行較長的執行時間，並讓您的應用程式執行速度變慢。 如果您使用 `Object` 變數做為實數值型別，則會產生*裝箱*和*取消裝箱*。 如果您將它用於參考型別，則會產生*晚期繫結*。  
  
## <a name="see-also"></a>另請參閱

- [類型字元](type-characters.md)
- [基礎資料類型](elementary-data-types.md)
- [數值資料類型](numeric-data-types.md)
- [字元資料類型](character-data-types.md)
- [疑難排解資料類型的問題](troubleshooting-data-types.md)
- [早期和晚期繫結](../early-late-binding/index.md)
