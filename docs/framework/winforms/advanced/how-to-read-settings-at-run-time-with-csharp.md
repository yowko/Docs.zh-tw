---
title: 如何：在執行階段使用的讀取設定C#
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], reading
- application settings [Windows Forms], run time
- application settings [Windows Forms], C#
ms.assetid: dbe8bf09-5e1c-49da-9192-154033d7240b
ms.openlocfilehash: d798b40e5e337ea7652c8e82cb7fa860a87528b9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54521747"
---
# <a name="how-to-read-settings-at-run-time-with-c"></a><span data-ttu-id="3641c-102">如何：在執行階段使用的讀取設定C#</span><span class="sxs-lookup"><span data-stu-id="3641c-102">How To: Read Settings at Run Time With C#</span></span> #
<span data-ttu-id="3641c-103">您可以在執行階段透過屬性物件來讀取應用程式範圍和使用者範圍的設定。</span><span class="sxs-lookup"><span data-stu-id="3641c-103">You can read both Application-scoped and User-scoped settings at run time via the Properties object.</span></span> <span data-ttu-id="3641c-104">屬性物件會透過 Properties.Settings.Default 成員公開所有專案的預設值。</span><span class="sxs-lookup"><span data-stu-id="3641c-104">The Properties object exposes all of the default settings for the project via the Properties.Settings.Default member.</span></span>  
  
### <a name="to-read-settings-at-run-time-with-c"></a><span data-ttu-id="3641c-105">在執行階段使用 C# 讀取設定</span><span class="sxs-lookup"><span data-stu-id="3641c-105">To Read Settings at Run Time with C#</span></span>  
  
-   <span data-ttu-id="3641c-106">透過 Properties.Settings.Default 成員存取適當的設定。</span><span class="sxs-lookup"><span data-stu-id="3641c-106">Access the appropriate setting via the Properties.Settings.Default member.</span></span> <span data-ttu-id="3641c-107">下列範例示範如何指派名為 `myColor` 的設定給 BackColor 屬性。</span><span class="sxs-lookup"><span data-stu-id="3641c-107">The following example shows how to assign a setting named `myColor` to a BackColor property.</span></span> <span data-ttu-id="3641c-108">它會要求您具有先前建立的設定檔，其中包含 `System.Drawing.Color` 類型之名為 `myColor` 的設定。</span><span class="sxs-lookup"><span data-stu-id="3641c-108">It requires you to have previously created a Settings file containing a setting named `myColor` of type `System.Drawing.Color`.</span></span> <span data-ttu-id="3641c-109">如需建立設定檔資訊，請參閱[How To:在設計階段建立新的設定](../../../../docs/framework/winforms/advanced/how-to-create-a-new-setting-at-design-time.md)。</span><span class="sxs-lookup"><span data-stu-id="3641c-109">For information about creating a Settings file, see [How To: Create a New Setting at Design Time](../../../../docs/framework/winforms/advanced/how-to-create-a-new-setting-at-design-time.md).</span></span>  
  
    ```  
    // C#  
    this.BackColor = Properties.Settings.Default.myColor;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="3641c-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3641c-110">See also</span></span>
- [<span data-ttu-id="3641c-111">使用應用程式設定和使用者設定</span><span class="sxs-lookup"><span data-stu-id="3641c-111">Using Application Settings and User Settings</span></span>](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)
- [<span data-ttu-id="3641c-112">如何：在執行階段撰寫使用者設定C#</span><span class="sxs-lookup"><span data-stu-id="3641c-112">How To: Write User Settings at Run Time with C#</span></span>](../../../../docs/framework/winforms/advanced/how-to-write-user-settings-at-run-time-with-csharp.md)
- [<span data-ttu-id="3641c-113">應用程式設定概觀</span><span class="sxs-lookup"><span data-stu-id="3641c-113">Application Settings Overview</span></span>](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
