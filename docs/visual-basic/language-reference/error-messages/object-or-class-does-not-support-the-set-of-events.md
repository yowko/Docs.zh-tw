---
title: 物件或類別不支援事件的設定
ms.date: 07/20/2015
f1_keywords:
- vbrID459
ms.assetid: 785df3f3-2aae-4a25-af36-1f9879d4e5fd
ms.openlocfilehash: bc75e031c2d05bea3aa64774a9d3817756e51e8b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409357"
---
# <a name="object-or-class-does-not-support-the-set-of-events"></a>物件或類別不支援事件的設定
您嘗試使用的 `WithEvents` 變數與元件無法做為指定事件集的事件來源。 例如，您想要接收物件的事件，然後建立第一個物件的另一個物件 `Implements` 。 雖然您可能會認為您可以從實作為物件接收事件，但這不一定都是如此。 `Implements`只會實作為方法和屬性的介面。 `WithEvents`不支援私 `UserControls` 用，因為 `ObjectEvent` 在執行時間無法使用引發所需的類型資訊。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 您無法接收不是來源事件之元件的事件。  
  
## <a name="see-also"></a>另請參閱

- [WithEvents](../modifiers/withevents.md)
- [Implements 陳述式](../statements/implements-statement.md)
