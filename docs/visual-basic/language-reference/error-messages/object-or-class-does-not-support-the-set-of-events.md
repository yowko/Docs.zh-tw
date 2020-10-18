---
title: 物件或類別不支援事件的設定
ms.date: 07/20/2015
f1_keywords:
- vbrID459
ms.assetid: 785df3f3-2aae-4a25-af36-1f9879d4e5fd
ms.openlocfilehash: c5e8b8de3477147fc3174cdbee401c89753004ad
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92159946"
---
# <a name="object-or-class-does-not-support-the-set-of-events"></a>物件或類別不支援事件的設定

您嘗試使用 `WithEvents` 具有元件的變數，而該元件無法做為指定事件集的事件來源。 例如，您想要接收物件的事件，然後建立第一個物件的另一個物件 `Implements` 。 雖然您可能會想要從已執行的物件接收事件，但是這不一定是如此。 `Implements` 只會針對方法和屬性執行介面。 `WithEvents` 不支援私 `UserControls` 用，因為 `ObjectEvent` 在執行時間無法使用引發所需的型別資訊。

## <a name="to-correct-this-error"></a>更正這個錯誤

- 您無法接收不是來源事件之元件的事件。

## <a name="see-also"></a>另請參閱

- [WithEvents](../modifiers/withevents.md)
- [Implements 陳述式](../statements/implements-statement.md)
