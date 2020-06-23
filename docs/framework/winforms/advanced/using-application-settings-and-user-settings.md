---
title: 使用應用程式設定和使用者設定
ms.date: 03/30/2017
description: 瞭解如何使用應用程式設定和使用者設定來建立和存取在應用程式執行會話之間保存的值。
helpviewer_keywords:
- user settings [Windows Forms]
- application settings [Windows Forms], how-to topics
ms.assetid: 54682d3b-1cbf-4683-9351-012b8b4286b5
ms.openlocfilehash: a30fd354986265eca002fce57bccf5b3bb2adc15
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903164"
---
# <a name="using-application-settings-and-user-settings"></a><span data-ttu-id="4b497-103">使用應用程式設定和使用者設定</span><span class="sxs-lookup"><span data-stu-id="4b497-103">Using Application Settings and User Settings</span></span>
<span data-ttu-id="4b497-104">從 .NET Framework 2.0 開始，您可以建立和存取在應用程式執行會話之間保存的值。</span><span class="sxs-lookup"><span data-stu-id="4b497-104">Starting with the .NET Framework 2.0, you can create and access values that are persisted between application execution sessions.</span></span> <span data-ttu-id="4b497-105">這些值稱為*設定*。</span><span class="sxs-lookup"><span data-stu-id="4b497-105">These values are called *settings*.</span></span> <span data-ttu-id="4b497-106">設定可以代表使用者喜好設定，或應用程式需要使用的重要資訊。</span><span class="sxs-lookup"><span data-stu-id="4b497-106">Settings can represent user preferences, or valuable information the application needs to use.</span></span> <span data-ttu-id="4b497-107">例如，您可能會建立一系列的設定，以儲存應用程式色彩配置的使用者喜好設定。</span><span class="sxs-lookup"><span data-stu-id="4b497-107">For example, you might create a series of settings that store user preferences for the color scheme of an application.</span></span> <span data-ttu-id="4b497-108">或者，您可以儲存連接字串來指定應用程式所使用的資料庫。</span><span class="sxs-lookup"><span data-stu-id="4b497-108">Or you might store the connection string that specifies a database that your application uses.</span></span> <span data-ttu-id="4b497-109">設定可讓您將對應用程式的重要資訊保存在程式碼外部，並建立儲存個別使用者喜好設定的設定檔。</span><span class="sxs-lookup"><span data-stu-id="4b497-109">Settings allow you to both persist information that is critical to the application outside the code, and to create profiles that store the preferences of individual users.</span></span>  
  
 <span data-ttu-id="4b497-110">本節中的主題描述如何在設計階段和執行時間使用設定。</span><span class="sxs-lookup"><span data-stu-id="4b497-110">The topics in this section describe how to use settings at design time and run time.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4b497-111">本節內容</span><span class="sxs-lookup"><span data-stu-id="4b497-111">In This Section</span></span>  
 [<span data-ttu-id="4b497-112">操作說明：在設計階段建立新設定</span><span class="sxs-lookup"><span data-stu-id="4b497-112">How To: Create a New Setting at Design Time</span></span>](how-to-create-a-new-setting-at-design-time.md)  
  
 <span data-ttu-id="4b497-113">說明如何使用 Visual Studio 來建立應用程式的新設定。</span><span class="sxs-lookup"><span data-stu-id="4b497-113">Explains how to use Visual Studio to create a new setting for an application.</span></span>  
  
 [<span data-ttu-id="4b497-114">如何：在設計階段變更現有設定的值</span><span class="sxs-lookup"><span data-stu-id="4b497-114">How To: Change the Value of an Existing Setting at Design Time</span></span>](how-to-change-the-value-of-an-existing-setting-at-design-time.md)  
  
 <span data-ttu-id="4b497-115">描述如何使用 Visual Studio 來變更現有設定的值。</span><span class="sxs-lookup"><span data-stu-id="4b497-115">Describes how to use Visual Studio to change the value of an existing setting.</span></span>  
  
 [<span data-ttu-id="4b497-116">如何：變更應用程式工作階段之間的設定值</span><span class="sxs-lookup"><span data-stu-id="4b497-116">How To: Change the Value of a Setting Between Application Sessions</span></span>](how-to-change-the-value-of-a-setting-between-application-sessions.md)  
  
 <span data-ttu-id="4b497-117">詳細說明如何在應用程式會話之間變更已編譯應用程式中的設定值。</span><span class="sxs-lookup"><span data-stu-id="4b497-117">Details how to change the value of a setting in a compiled application between application sessions.</span></span>  
  
 [<span data-ttu-id="4b497-118">如何：在執行階段使用 C# 讀取設定</span><span class="sxs-lookup"><span data-stu-id="4b497-118">How To: Read Settings at Run Time With C#</span></span>](how-to-read-settings-at-run-time-with-csharp.md)  
  
 <span data-ttu-id="4b497-119">描述如何使用程式碼，以 c # 來讀取設定。</span><span class="sxs-lookup"><span data-stu-id="4b497-119">Describes how to use code to read settings with C#.</span></span>  
  
 [<span data-ttu-id="4b497-120">操作說明：在執行階段使用 C# 撰寫使用者設定</span><span class="sxs-lookup"><span data-stu-id="4b497-120">How To: Write User Settings at Run Time with C#</span></span>](how-to-write-user-settings-at-run-time-with-csharp.md)  
  
 <span data-ttu-id="4b497-121">說明如何使用程式碼，以 c # 撰寫和儲存使用者設定的值。</span><span class="sxs-lookup"><span data-stu-id="4b497-121">Explains how to use code to write and save the values of user settings with C#.</span></span>  
  
 [<span data-ttu-id="4b497-122">操作說明：在 C# 中將多組設定加入至應用程式</span><span class="sxs-lookup"><span data-stu-id="4b497-122">How To: Add Multiple Sets of Settings To Your Application in C#</span></span>](how-to-add-multiple-sets-of-settings-to-your-application-in-csharp.md)  
  
 <span data-ttu-id="4b497-123">詳細說明如何使用 c # 將多組設定加入至應用程式。</span><span class="sxs-lookup"><span data-stu-id="4b497-123">Details how to add multiple sets of settings to an application with C#.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b497-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4b497-124">See also</span></span>

- [<span data-ttu-id="4b497-125">Windows Forms 的應用程式設定</span><span class="sxs-lookup"><span data-stu-id="4b497-125">Application Settings for Windows Forms</span></span>](application-settings-for-windows-forms.md)
