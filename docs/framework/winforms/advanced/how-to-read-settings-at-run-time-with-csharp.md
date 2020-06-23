---
title: 如何：在執行階段使用 C# 讀取設定
description: '瞭解如何透過 Properties 物件，在執行時間使用 c # 讀取應用程式範圍和使用者範圍的設定。'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], reading
- application settings [Windows Forms], run time
- application settings [Windows Forms], C#
ms.assetid: dbe8bf09-5e1c-49da-9192-154033d7240b
ms.openlocfilehash: d784544e018bb693c501e35ea36fcae1946ef5eb
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903347"
---
# <a name="how-to-read-settings-at-run-time-with-c"></a><span data-ttu-id="35f8e-103">如何：在執行時間使用 C 讀取設定\#</span><span class="sxs-lookup"><span data-stu-id="35f8e-103">How To: Read Settings at Run Time With C\#</span></span>

<span data-ttu-id="35f8e-104">您可以在執行階段透過屬性物件來讀取應用程式範圍和使用者範圍的設定。</span><span class="sxs-lookup"><span data-stu-id="35f8e-104">You can read both Application-scoped and User-scoped settings at run time via the Properties object.</span></span> <span data-ttu-id="35f8e-105">Properties 物件會透過其定義所在之專案的預設命名空間中的屬性，來公開專案的所有預設設定。</span><span class="sxs-lookup"><span data-stu-id="35f8e-105">The Properties object exposes all of the default settings for the project via the Properties.Settings.Default member in the default namespace of the project they are defined in.</span></span>  
  
## <a name="to-read-settings-at-run-time-with-c"></a><span data-ttu-id="35f8e-106">若要在執行時間使用 C 讀取設定\#</span><span class="sxs-lookup"><span data-stu-id="35f8e-106">To Read Settings at Run Time with C\#</span></span>
  
<span data-ttu-id="35f8e-107">透過 Properties.Settings.Default 成員存取適當的設定。</span><span class="sxs-lookup"><span data-stu-id="35f8e-107">Access the appropriate setting via the Properties.Settings.Default member.</span></span> <span data-ttu-id="35f8e-108">下列範例示範如何指派名為 `myColor` 的設定給 BackColor 屬性。</span><span class="sxs-lookup"><span data-stu-id="35f8e-108">The following example shows how to assign a setting named `myColor` to a BackColor property.</span></span> <span data-ttu-id="35f8e-109">它會要求您具有先前建立的設定檔，其中包含 `System.Drawing.Color` 類型之名為 `myColor` 的設定。</span><span class="sxs-lookup"><span data-stu-id="35f8e-109">It requires you to have previously created a Settings file containing a setting named `myColor` of type `System.Drawing.Color`.</span></span> <span data-ttu-id="35f8e-110">如需建立設定檔的相關資訊，請參閱[如何：在設計階段建立新設定](how-to-create-a-new-setting-at-design-time.md)。</span><span class="sxs-lookup"><span data-stu-id="35f8e-110">For information about creating a Settings file, see [How To: Create a New Setting at Design Time](how-to-create-a-new-setting-at-design-time.md).</span></span>  
  
```csharp
this.BackColor = Properties.Settings.Default.myColor;  
```  
  
## <a name="see-also"></a><span data-ttu-id="35f8e-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="35f8e-111">See also</span></span>

- [<span data-ttu-id="35f8e-112">使用應用程式設定和使用者設定</span><span class="sxs-lookup"><span data-stu-id="35f8e-112">Using Application Settings and User Settings</span></span>](using-application-settings-and-user-settings.md)
- [<span data-ttu-id="35f8e-113">操作說明：在執行階段使用 C# 撰寫使用者設定</span><span class="sxs-lookup"><span data-stu-id="35f8e-113">How To: Write User Settings at Run Time with C#</span></span>](how-to-write-user-settings-at-run-time-with-csharp.md)
- [<span data-ttu-id="35f8e-114">應用程式設定總覽</span><span class="sxs-lookup"><span data-stu-id="35f8e-114">Application Settings Overview</span></span>](application-settings-overview.md)
