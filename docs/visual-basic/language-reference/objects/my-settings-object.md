---
title: My.Settings 物件
ms.date: 07/20/2015
f1_keywords:
- My.MySettingsProperty.Settings
- My.Settings
helpviewer_keywords:
- My.Settings object
ms.assetid: 41f30dc1-202a-4273-b9b7-5728941f996c
ms.openlocfilehash: 9560a51332ea596d4cf2228f1e07c158a0457ece
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350350"
---
# <a name="mysettings-object"></a><span data-ttu-id="e3e05-102">My.Settings 物件</span><span class="sxs-lookup"><span data-stu-id="e3e05-102">My.Settings Object</span></span>
<span data-ttu-id="e3e05-103">Provides properties and methods for accessing the application's settings.</span><span class="sxs-lookup"><span data-stu-id="e3e05-103">Provides properties and methods for accessing the application's settings.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e3e05-104">備註</span><span class="sxs-lookup"><span data-stu-id="e3e05-104">Remarks</span></span>  
 <span data-ttu-id="e3e05-105">The `My.Settings` object provides access to the application's settings and allows you to dynamically store and retrieve property settings and other information for your application.</span><span class="sxs-lookup"><span data-stu-id="e3e05-105">The `My.Settings` object provides access to the application's settings and allows you to dynamically store and retrieve property settings and other information for your application.</span></span> <span data-ttu-id="e3e05-106">如需詳細資訊，請參閱[管理應用程式設定 (.NET)](/visualstudio/ide/managing-application-settings-dotnet)。</span><span class="sxs-lookup"><span data-stu-id="e3e05-106">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="properties"></a><span data-ttu-id="e3e05-107">內容</span><span class="sxs-lookup"><span data-stu-id="e3e05-107">Properties</span></span>  
 <span data-ttu-id="e3e05-108">`My.Settings` 物件的屬性可存取您應用程式的設定。</span><span class="sxs-lookup"><span data-stu-id="e3e05-108">The properties of the `My.Settings` object provide access to your application's settings.</span></span> <span data-ttu-id="e3e05-109">To add or remove settings, use the **Settings Designer**.</span><span class="sxs-lookup"><span data-stu-id="e3e05-109">To add or remove settings, use the **Settings Designer**.</span></span>  
  
 <span data-ttu-id="e3e05-110">Each setting has a **Name**, **Type**, **Scope**, and **Value**, and these settings determine how the property to access each setting appears in the `My.Settings` object:</span><span class="sxs-lookup"><span data-stu-id="e3e05-110">Each setting has a **Name**, **Type**, **Scope**, and **Value**, and these settings determine how the property to access each setting appears in the `My.Settings` object:</span></span>  
  
- <span data-ttu-id="e3e05-111">**Name** determines the name of the property.</span><span class="sxs-lookup"><span data-stu-id="e3e05-111">**Name** determines the name of the property.</span></span>  
  
- <span data-ttu-id="e3e05-112">**Type** determines the type of the property.</span><span class="sxs-lookup"><span data-stu-id="e3e05-112">**Type** determines the type of the property.</span></span>  
  
- <span data-ttu-id="e3e05-113">**Scope** indicates if the property is read-only.</span><span class="sxs-lookup"><span data-stu-id="e3e05-113">**Scope** indicates if the property is read-only.</span></span> <span data-ttu-id="e3e05-114">If the value is **Application**, the property is read-only; if the value is **User**, the property is read-write.</span><span class="sxs-lookup"><span data-stu-id="e3e05-114">If the value is **Application**, the property is read-only; if the value is **User**, the property is read-write.</span></span>  
  
- <span data-ttu-id="e3e05-115">**Value** is the default value of the property.</span><span class="sxs-lookup"><span data-stu-id="e3e05-115">**Value** is the default value of the property.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e3e05-116">方法</span><span class="sxs-lookup"><span data-stu-id="e3e05-116">Methods</span></span>  
  
|<span data-ttu-id="e3e05-117">方法</span><span class="sxs-lookup"><span data-stu-id="e3e05-117">Method</span></span>|<span data-ttu-id="e3e05-118">描述</span><span class="sxs-lookup"><span data-stu-id="e3e05-118">Description</span></span>|  
|---|---|  
|`Reload`|<span data-ttu-id="e3e05-119">Reloads the user settings from the last saved values.</span><span class="sxs-lookup"><span data-stu-id="e3e05-119">Reloads the user settings from the last saved values.</span></span>|  
|`Save`|<span data-ttu-id="e3e05-120">Saves the current user settings.</span><span class="sxs-lookup"><span data-stu-id="e3e05-120">Saves the current user settings.</span></span>|  
  
 <span data-ttu-id="e3e05-121">The `My.Settings` object also provides advanced properties and methods, inherited from the <xref:System.Configuration.ApplicationSettingsBase> class.</span><span class="sxs-lookup"><span data-stu-id="e3e05-121">The `My.Settings` object also provides advanced properties and methods, inherited from the <xref:System.Configuration.ApplicationSettingsBase> class.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="e3e05-122">工作</span><span class="sxs-lookup"><span data-stu-id="e3e05-122">Tasks</span></span>  
 <span data-ttu-id="e3e05-123">The following table lists examples of tasks involving the `My.Settings` object.</span><span class="sxs-lookup"><span data-stu-id="e3e05-123">The following table lists examples of tasks involving the `My.Settings` object.</span></span>  
  
|<span data-ttu-id="e3e05-124">若要</span><span class="sxs-lookup"><span data-stu-id="e3e05-124">To</span></span>|<span data-ttu-id="e3e05-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="e3e05-125">See</span></span>|  
|---|---|  
|<span data-ttu-id="e3e05-126">Read an application setting</span><span class="sxs-lookup"><span data-stu-id="e3e05-126">Read an application setting</span></span>|[<span data-ttu-id="e3e05-127">如何：在 Visual Basic 中讀取應用程式設定</span><span class="sxs-lookup"><span data-stu-id="e3e05-127">How to: Read Application Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)|  
|<span data-ttu-id="e3e05-128">Change a user setting</span><span class="sxs-lookup"><span data-stu-id="e3e05-128">Change a user setting</span></span>|[<span data-ttu-id="e3e05-129">如何：在 Visual Basic 中變更使用者設定</span><span class="sxs-lookup"><span data-stu-id="e3e05-129">How to: Change User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)|  
|<span data-ttu-id="e3e05-130">Persist user settings</span><span class="sxs-lookup"><span data-stu-id="e3e05-130">Persist user settings</span></span>|[<span data-ttu-id="e3e05-131">如何：保存 Visual Basic 中的使用者設定</span><span class="sxs-lookup"><span data-stu-id="e3e05-131">How to: Persist User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)|  
|<span data-ttu-id="e3e05-132">Create a property grid for user settings</span><span class="sxs-lookup"><span data-stu-id="e3e05-132">Create a property grid for user settings</span></span>|[<span data-ttu-id="e3e05-133">如何：在 Visual Basic 中建立使用者設定的屬性方格</span><span class="sxs-lookup"><span data-stu-id="e3e05-133">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)|  
  
## <a name="example"></a><span data-ttu-id="e3e05-134">範例</span><span class="sxs-lookup"><span data-stu-id="e3e05-134">Example</span></span>  
 <span data-ttu-id="e3e05-135">此範例會顯示 `Nickname` 設定的值。</span><span class="sxs-lookup"><span data-stu-id="e3e05-135">This example displays the value of the `Nickname` setting.</span></span>  
  
 [!code-vb[VbVbalrMyResources#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#14)]  
  
 <span data-ttu-id="e3e05-136">為了確保此範例正常運作，您的應用程式必須具有 `String` 類型的 `Nickname` 設定。</span><span class="sxs-lookup"><span data-stu-id="e3e05-136">For this example to work, your application must have a `Nickname` setting, of type `String`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3e05-137">請參閱</span><span class="sxs-lookup"><span data-stu-id="e3e05-137">See also</span></span>

- <xref:System.Configuration.ApplicationSettingsBase>
- [<span data-ttu-id="e3e05-138">如何：在 Visual Basic 中讀取應用程式設定</span><span class="sxs-lookup"><span data-stu-id="e3e05-138">How to: Read Application Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [<span data-ttu-id="e3e05-139">如何：在 Visual Basic 中變更使用者設定</span><span class="sxs-lookup"><span data-stu-id="e3e05-139">How to: Change User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [<span data-ttu-id="e3e05-140">如何：保存 Visual Basic 中的使用者設定</span><span class="sxs-lookup"><span data-stu-id="e3e05-140">How to: Persist User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [<span data-ttu-id="e3e05-141">如何：在 Visual Basic 中建立使用者設定的屬性方格</span><span class="sxs-lookup"><span data-stu-id="e3e05-141">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="e3e05-142">管理應用程式設定 (.NET)</span><span class="sxs-lookup"><span data-stu-id="e3e05-142">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
