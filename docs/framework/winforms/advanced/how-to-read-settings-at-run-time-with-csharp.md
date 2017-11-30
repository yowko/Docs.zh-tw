---
title: "如何：在執行階段使用 C# 讀取設定"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application settings [Windows Forms], reading
- application settings [Windows Forms], run time
- application settings [Windows Forms], C#
ms.assetid: dbe8bf09-5e1c-49da-9192-154033d7240b
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9c23fd88d33ff4ca480c435f2058f4c568320578
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-settings-at-run-time-with-c"></a><span data-ttu-id="b3a4a-102">如何：在執行階段使用 C# 讀取設定</span><span class="sxs-lookup"><span data-stu-id="b3a4a-102">How To: Read Settings at Run Time With C#</span></span> #
<span data-ttu-id="b3a4a-103">您可以在執行階段透過屬性物件來讀取應用程式範圍和使用者範圍的設定。</span><span class="sxs-lookup"><span data-stu-id="b3a4a-103">You can read both Application-scoped and User-scoped settings at run time via the Properties object.</span></span> <span data-ttu-id="b3a4a-104">屬性物件會透過 Properties.Settings.Default 成員公開所有專案的預設值。</span><span class="sxs-lookup"><span data-stu-id="b3a4a-104">The Properties object exposes all of the default settings for the project via the Properties.Settings.Default member.</span></span>  
  
### <a name="to-read-settings-at-run-time-with-c"></a><span data-ttu-id="b3a4a-105">在執行階段使用 C# 讀取設定</span><span class="sxs-lookup"><span data-stu-id="b3a4a-105">To Read Settings at Run Time with C#</span></span>  
  
-   <span data-ttu-id="b3a4a-106">透過 Properties.Settings.Default 成員存取適當的設定。</span><span class="sxs-lookup"><span data-stu-id="b3a4a-106">Access the appropriate setting via the Properties.Settings.Default member.</span></span> <span data-ttu-id="b3a4a-107">下列範例示範如何指派名為 `myColor` 的設定給 BackColor 屬性。</span><span class="sxs-lookup"><span data-stu-id="b3a4a-107">The following example shows how to assign a setting named `myColor` to a BackColor property.</span></span> <span data-ttu-id="b3a4a-108">它會要求您具有先前建立的設定檔，其中包含 `System.Drawing.Color` 類型之名為 `myColor` 的設定。</span><span class="sxs-lookup"><span data-stu-id="b3a4a-108">It requires you to have previously created a Settings file containing a setting named `myColor` of type `System.Drawing.Color`.</span></span> <span data-ttu-id="b3a4a-109">如需建立設定檔資訊，請參閱[How To： 在設計階段建立新的設定](../../../../docs/framework/winforms/advanced/how-to-create-a-new-setting-at-design-time.md)。</span><span class="sxs-lookup"><span data-stu-id="b3a4a-109">For information about creating a Settings file, see [How To: Create a New Setting at Design Time](../../../../docs/framework/winforms/advanced/how-to-create-a-new-setting-at-design-time.md).</span></span>  
  
    ```  
    // C#  
    this.BackColor = Properties.Settings.Default.myColor;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="b3a4a-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b3a4a-110">See Also</span></span>  
 [<span data-ttu-id="b3a4a-111">使用應用程式設定和使用者設定</span><span class="sxs-lookup"><span data-stu-id="b3a4a-111">Using Application Settings and User Settings</span></span>](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)  
 [<span data-ttu-id="b3a4a-112">操作說明：在執行階段使用 C# 撰寫使用者設定</span><span class="sxs-lookup"><span data-stu-id="b3a4a-112">How To: Write User Settings at Run Time with C#</span></span>](../../../../docs/framework/winforms/advanced/how-to-write-user-settings-at-run-time-with-csharp.md)  
 [<span data-ttu-id="b3a4a-113">應用程式設定概觀</span><span class="sxs-lookup"><span data-stu-id="b3a4a-113">Application Settings Overview</span></span>](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
