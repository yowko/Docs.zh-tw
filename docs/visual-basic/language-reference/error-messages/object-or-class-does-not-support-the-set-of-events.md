---
title: "物件或類別不支援事件的設定"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID459
ms.assetid: 785df3f3-2aae-4a25-af36-1f9879d4e5fd
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: be4b9140222ef969bfb836fd74f45b8f662360b8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="object-or-class-does-not-support-the-set-of-events"></a>物件或類別不支援事件的設定
您嘗試使用`WithEvents`變數無法為指定的事件集的事件來源的元件。 例如，您要接收到事件的物件，然後再建立另一個物件`Implements`的第一個物件。 您可能會認為您可以從實作的物件接收到事件，但這不一定大小寫。 `Implements`只會實作介面方法和屬性。 `WithEvents`不支援私用`UserControls`，因為型別資訊所需引發`ObjectEvent`不在執行階段。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  您無法接收事件的來源元件。  
  
## <a name="see-also"></a>另請參閱  
 [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)  
 [Implements 陳述式](../../../visual-basic/language-reference/statements/implements-statement.md)
