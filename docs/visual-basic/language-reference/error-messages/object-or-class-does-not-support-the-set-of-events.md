---
title: 物件或類別不支援事件的設定
ms.date: 07/20/2015
f1_keywords:
- vbrID459
ms.assetid: 785df3f3-2aae-4a25-af36-1f9879d4e5fd
ms.openlocfilehash: e55a5515d88bd2782e31fdea7c07e16c595d43b5
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873651"
---
# <a name="object-or-class-does-not-support-the-set-of-events"></a>物件或類別不支援事件的設定

您嘗試使用 `WithEvents` 具有元件的變數，而該元件無法做為指定事件集的事件來源。 例如，您想要接收物件的事件，然後建立第一個物件的另一個物件 `Implements` 。 雖然您可能會想要從已執行的物件接收事件，但是這不一定是如此。 `Implements` 只會針對方法和屬性執行介面。 `WithEvents` 不支援私 `UserControls` 用，因為 `ObjectEvent` 在執行時間無法使用引發所需的型別資訊。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 您無法接收不是來源事件之元件的事件。  
  
## <a name="see-also"></a>另請參閱

- [WithEvents](../modifiers/withevents.md)
- [Implements 陳述式](../statements/implements-statement.md)
