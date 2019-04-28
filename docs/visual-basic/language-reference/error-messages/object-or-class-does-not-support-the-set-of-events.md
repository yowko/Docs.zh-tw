---
title: 物件或類別不支援事件的設定
ms.date: 07/20/2015
f1_keywords:
- vbrID459
ms.assetid: 785df3f3-2aae-4a25-af36-1f9879d4e5fd
ms.openlocfilehash: ad9176b5332a75f03968e742501c3fce541055de
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61925758"
---
# <a name="object-or-class-does-not-support-the-set-of-events"></a>物件或類別不支援事件的設定
您嘗試使用`WithEvents`變數無法為指定的事件集的事件來源的元件。 例如，您要接收事件的物件，然後建立另一個物件`Implements`的第一個物件。 您可能會認為您可以從實作的物件來接收事件，但這不一定如此。 `Implements` 只會實作的介面方法和屬性。 `WithEvents` 不支援私用`UserControls`，因為型別資訊才能引發`ObjectEvent`不在執行階段。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 您不能接收事件的來源元件。  
  
## <a name="see-also"></a>另請參閱

- [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)
- [Implements 陳述式](../../../visual-basic/language-reference/statements/implements-statement.md)
