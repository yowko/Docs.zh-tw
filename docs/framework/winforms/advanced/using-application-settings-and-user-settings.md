---
title: 使用應用程式設定和使用者設定
ms.date: 03/30/2017
helpviewer_keywords:
- user settings [Windows Forms]
- application settings [Windows Forms], how-to topics
ms.assetid: 54682d3b-1cbf-4683-9351-012b8b4286b5
ms.openlocfilehash: f5231ecc9fb3898d60241ea8a53b509daced8a0f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33523838"
---
# <a name="using-application-settings-and-user-settings"></a><span data-ttu-id="bb41d-102">使用應用程式設定和使用者設定</span><span class="sxs-lookup"><span data-stu-id="bb41d-102">Using Application Settings and User Settings</span></span>
<span data-ttu-id="bb41d-103">從.NET Framework 2.0 開始，您可以建立並存取應用程式執行的工作階段之間保存的值。</span><span class="sxs-lookup"><span data-stu-id="bb41d-103">Starting with the .NET Framework 2.0, you can create and access values that are persisted between application execution sessions.</span></span> <span data-ttu-id="bb41d-104">這些值稱為*設定*。</span><span class="sxs-lookup"><span data-stu-id="bb41d-104">These values are called *settings*.</span></span> <span data-ttu-id="bb41d-105">設定可以代表使用者喜好設定，或需要使用應用程式的重要資訊。</span><span class="sxs-lookup"><span data-stu-id="bb41d-105">Settings can represent user preferences, or valuable information the application needs to use.</span></span> <span data-ttu-id="bb41d-106">例如，您可能會建立一系列的應用程式的色彩配置的使用者喜好設定儲存的設定。</span><span class="sxs-lookup"><span data-stu-id="bb41d-106">For example, you might create a series of settings that store user preferences for the color scheme of an application.</span></span> <span data-ttu-id="bb41d-107">或者，您可能會儲存連接字串，指定您的應用程式使用的資料庫。</span><span class="sxs-lookup"><span data-stu-id="bb41d-107">Or you might store the connection string that specifies a database that your application uses.</span></span> <span data-ttu-id="bb41d-108">設定可讓您保留很重要的應用程式外部程式碼，以及建立儲存個別使用者的喜好設定的設定檔的資訊。</span><span class="sxs-lookup"><span data-stu-id="bb41d-108">Settings allow you to both persist information that is critical to the application outside the code, and to create profiles that store the preferences of individual users.</span></span>  
  
 <span data-ttu-id="bb41d-109">本節中的主題描述如何在設計階段使用的設定和執行階段。</span><span class="sxs-lookup"><span data-stu-id="bb41d-109">The topics in this section describe how to use settings at design time and run time.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bb41d-110">本節內容</span><span class="sxs-lookup"><span data-stu-id="bb41d-110">In This Section</span></span>  
 [<span data-ttu-id="bb41d-111">操作說明：在設計階段建立新設定</span><span class="sxs-lookup"><span data-stu-id="bb41d-111">How To: Create a New Setting at Design Time</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-a-new-setting-at-design-time.md)  
  
 <span data-ttu-id="bb41d-112">說明如何使用 Visual Studio 來建立新的應用程式設定。</span><span class="sxs-lookup"><span data-stu-id="bb41d-112">Explains how to use Visual Studio to create a new setting for an application.</span></span>  
  
 [<span data-ttu-id="bb41d-113">操作說明：在設計階段變更現有設定的值</span><span class="sxs-lookup"><span data-stu-id="bb41d-113">How To: Change the Value of an Existing Setting at Design Time</span></span>](../../../../docs/framework/winforms/advanced/how-to-change-the-value-of-an-existing-setting-at-design-time.md)  
  
 <span data-ttu-id="bb41d-114">描述如何使用 Visual Studio 來變更現有的設定值。</span><span class="sxs-lookup"><span data-stu-id="bb41d-114">Describes how to use Visual Studio to change the value of an existing setting.</span></span>  
  
 [<span data-ttu-id="bb41d-115">操作說明：變更應用程式工作階段之間的設定值</span><span class="sxs-lookup"><span data-stu-id="bb41d-115">How To: Change the Value of a Setting Between Application Sessions</span></span>](../../../../docs/framework/winforms/advanced/how-to-change-the-value-of-a-setting-between-application-sessions.md)  
  
 <span data-ttu-id="bb41d-116">詳細說明如何變更應用程式工作階段之間的編譯應用程式中設定的值。</span><span class="sxs-lookup"><span data-stu-id="bb41d-116">Details how to change the value of a setting in a compiled application between application sessions.</span></span>  
  
 [<span data-ttu-id="bb41d-117">操作說明：在執行階段使用 C# 讀取設定</span><span class="sxs-lookup"><span data-stu-id="bb41d-117">How To: Read Settings at Run Time With C#</span></span>](../../../../docs/framework/winforms/advanced/how-to-read-settings-at-run-time-with-csharp.md)  
  
 <span data-ttu-id="bb41d-118">描述如何使用程式碼來讀取使用 C# 的設定。</span><span class="sxs-lookup"><span data-stu-id="bb41d-118">Describes how to use code to read settings with C#.</span></span>  
  
 [<span data-ttu-id="bb41d-119">操作說明：在執行階段使用 C# 撰寫使用者設定</span><span class="sxs-lookup"><span data-stu-id="bb41d-119">How To: Write User Settings at Run Time with C#</span></span>](../../../../docs/framework/winforms/advanced/how-to-write-user-settings-at-run-time-with-csharp.md)  
  
 <span data-ttu-id="bb41d-120">說明如何使用程式碼撰寫，並使用 C# 中儲存使用者設定的值。</span><span class="sxs-lookup"><span data-stu-id="bb41d-120">Explains how to use code to write and save the values of user settings with C#.</span></span>  
  
 [<span data-ttu-id="bb41d-121">操作說明：在 C# 中將多組設定加入至應用程式</span><span class="sxs-lookup"><span data-stu-id="bb41d-121">How To: Add Multiple Sets of Settings To Your Application in C#</span></span>](../../../../docs/framework/winforms/advanced/how-to-add-multiple-sets-of-settings-to-your-application-in-csharp.md)  
  
 <span data-ttu-id="bb41d-122">詳細說明如何使用 C# 應用程式中加入多組設定。</span><span class="sxs-lookup"><span data-stu-id="bb41d-122">Details how to add multiple sets of settings to an application with C#.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb41d-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bb41d-123">See Also</span></span>  
 [<span data-ttu-id="bb41d-124">Windows Forms 的應用程式設定</span><span class="sxs-lookup"><span data-stu-id="bb41d-124">Application Settings for Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/application-settings-for-windows-forms.md)
