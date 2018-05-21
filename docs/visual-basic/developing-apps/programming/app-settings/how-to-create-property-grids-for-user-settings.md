---
title: 如何：在 Visual Basic 中建立使用者設定的屬性方格
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], creating property grids for user settings
- user settings [Visual Basic], creating property grids
- property grids [Visual Basic], creating for user settings
- property grids
ms.assetid: b0bc737e-50d1-43d1-a6df-268db6e6f91c
ms.openlocfilehash: c03e7c6138633287506ff01128a1e2acb321b02d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-property-grids-for-user-settings-in-visual-basic"></a><span data-ttu-id="8aa2b-102">如何：在 Visual Basic 中建立使用者設定的屬性方格</span><span class="sxs-lookup"><span data-stu-id="8aa2b-102">How to: Create Property Grids for User Settings in Visual Basic</span></span>
<span data-ttu-id="8aa2b-103">您可以使用 `My.Settings` 物件的使用者設定屬性填入 <xref:System.Windows.Forms.PropertyGrid> 控制項，以建立使用者設定的屬性方格。</span><span class="sxs-lookup"><span data-stu-id="8aa2b-103">You can create a property grid for user settings by populating a <xref:System.Windows.Forms.PropertyGrid> control with the user setting properties of the `My.Settings` object.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8aa2b-104">為了確保此範例正常運作，您的應用程式必須已設定其使用者設定。</span><span class="sxs-lookup"><span data-stu-id="8aa2b-104">In order for this example to work, your application must have its user settings configured.</span></span> <span data-ttu-id="8aa2b-105">如需詳細資訊，請參閱[管理應用程式設定 (.NET)](/visualstudio/ide/managing-application-settings-dotnet)。</span><span class="sxs-lookup"><span data-stu-id="8aa2b-105">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
 <span data-ttu-id="8aa2b-106">`My.Settings` 物件會將每項設定公開為屬性。</span><span class="sxs-lookup"><span data-stu-id="8aa2b-106">The `My.Settings` object exposes each setting as a property.</span></span> <span data-ttu-id="8aa2b-107">屬性名稱與設定名稱相同，而屬性類型與設定類型相同。</span><span class="sxs-lookup"><span data-stu-id="8aa2b-107">The property name is the same as the setting name, and the property type is the same as the setting type.</span></span> <span data-ttu-id="8aa2b-108">設定的 [範圍] 可判斷屬性是否為唯讀；[應用程式] 範圍設定的屬性為唯讀，而 [使用者] 範圍設定的屬性為讀寫。</span><span class="sxs-lookup"><span data-stu-id="8aa2b-108">The setting's **Scope** determines if the property is read-only; the property for an **Application**-scope setting is read-only, while the property for a **User**-scope setting is read-write.</span></span> <span data-ttu-id="8aa2b-109">如需詳細資訊，請參閱 [My.Settings 物件](../../../../visual-basic/language-reference/objects/my-settings-object.md)。</span><span class="sxs-lookup"><span data-stu-id="8aa2b-109">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8aa2b-110">您無法在執行階段變更或儲存應用程式範圍設定的值。</span><span class="sxs-lookup"><span data-stu-id="8aa2b-110">You cannot change or save the values of application-scope settings at run time.</span></span> <span data-ttu-id="8aa2b-111">只有在建立應用程式時 (透過 [專案設計工具]或藉由編輯應用程式的組態檔)，才能變更應用程式範圍的設定。</span><span class="sxs-lookup"><span data-stu-id="8aa2b-111">Application-scope settings can be changed only when creating the application (through the **Project Designer**) or by editing the application's configuration file.</span></span> <span data-ttu-id="8aa2b-112">如需詳細資訊，請參閱[管理應用程式設定 (.NET)](/visualstudio/ide/managing-application-settings-dotnet)。</span><span class="sxs-lookup"><span data-stu-id="8aa2b-112">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
 <span data-ttu-id="8aa2b-113">此範例會使用 <xref:System.Windows.Forms.PropertyGrid> 控制項來存取 `My.Settings` 物件的使用者設定屬性。</span><span class="sxs-lookup"><span data-stu-id="8aa2b-113">This example uses a <xref:System.Windows.Forms.PropertyGrid> control to access the user-setting properties of the `My.Settings` object.</span></span> <span data-ttu-id="8aa2b-114"><xref:System.Windows.Forms.PropertyGrid> 預設會顯示 `My.Settings` 物件的所有屬性。</span><span class="sxs-lookup"><span data-stu-id="8aa2b-114">By default, the <xref:System.Windows.Forms.PropertyGrid> shows all the properties of the `My.Settings` object.</span></span> <span data-ttu-id="8aa2b-115">不過，使用者設定屬性有 <xref:System.Configuration.UserScopedSettingAttribute> 屬性。</span><span class="sxs-lookup"><span data-stu-id="8aa2b-115">However, the user-setting properties have the <xref:System.Configuration.UserScopedSettingAttribute> attribute.</span></span> <span data-ttu-id="8aa2b-116">此範例會將 <xref:System.Windows.Forms.PropertyGrid> 的 <xref:System.Windows.Forms.PropertyGrid.BrowsableAttributes%2A> 屬性設定為 <xref:System.Configuration.UserScopedSettingAttribute> 以只顯示使用者設定屬性。</span><span class="sxs-lookup"><span data-stu-id="8aa2b-116">This example sets the <xref:System.Windows.Forms.PropertyGrid.BrowsableAttributes%2A> property of the <xref:System.Windows.Forms.PropertyGrid> to <xref:System.Configuration.UserScopedSettingAttribute> to display only the user-setting properties.</span></span>  
  
### <a name="to-add-a-user-setting-property-grid"></a><span data-ttu-id="8aa2b-117">新增使用者設定屬性方格</span><span class="sxs-lookup"><span data-stu-id="8aa2b-117">To add a user setting property grid</span></span>  
  
1.  <span data-ttu-id="8aa2b-118">將 PropertyGrid 控制項從 [工具箱] 新增至應用程式 (此處假設為 `Form1`) 的設計介面。</span><span class="sxs-lookup"><span data-stu-id="8aa2b-118">Add the **PropertyGrid** control from the **Toolbox** to the design surface for your application, assumed here to be `Form1`.</span></span>  
  
     <span data-ttu-id="8aa2b-119">屬性方格控制項的預設名稱為 `PropertyGrid1`。</span><span class="sxs-lookup"><span data-stu-id="8aa2b-119">The default name of the property-grid control is `PropertyGrid1`.</span></span>  
  
2.  <span data-ttu-id="8aa2b-120">按兩下 `Form1` 的設計介面，以開啟表單載入事件處理常式的程式碼。</span><span class="sxs-lookup"><span data-stu-id="8aa2b-120">Double-click the design surface for `Form1` to open the code for the form-load event handler.</span></span>  
  
3.  <span data-ttu-id="8aa2b-121">將 `My.Settings` 物件設定為屬性方格的選取物件。</span><span class="sxs-lookup"><span data-stu-id="8aa2b-121">Set the `My.Settings` object as the selected object for the property grid.</span></span>  
  
     [!code-vb[VbVbalrMyResources#11](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-create-property-grids-for-user-settings_1.vb)]  
  
4.  <span data-ttu-id="8aa2b-122">將屬性方格設定為只顯示使用者設定。</span><span class="sxs-lookup"><span data-stu-id="8aa2b-122">Configure the property grid to show only the user settings.</span></span>  
  
     [!code-vb[VbVbalrMyResources#12](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-create-property-grids-for-user-settings_2.vb)]  
  
    > [!NOTE]
    >  <span data-ttu-id="8aa2b-123">若只要顯示應用程式範圍的設定，請使用 <xref:System.Configuration.ApplicationScopedSettingAttribute> 屬性而不是 <xref:System.Configuration.UserScopedSettingAttribute>。</span><span class="sxs-lookup"><span data-stu-id="8aa2b-123">To show only the application-scope settings, use the <xref:System.Configuration.ApplicationScopedSettingAttribute> attribute instead of  <xref:System.Configuration.UserScopedSettingAttribute>.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="8aa2b-124">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="8aa2b-124">Robust Programming</span></span>  
 <span data-ttu-id="8aa2b-125">應用程式關閉時，會儲存使用者設定。</span><span class="sxs-lookup"><span data-stu-id="8aa2b-125">The application saves the user settings when the application shuts down.</span></span> <span data-ttu-id="8aa2b-126">若要立即儲存設定，請呼叫 `My.Settings.Save` 方法。</span><span class="sxs-lookup"><span data-stu-id="8aa2b-126">To save the settings immediately, call the `My.Settings.Save` method.</span></span> <span data-ttu-id="8aa2b-127">如需詳細資訊，請參閱[如何：保存 Visual Basic 中的使用者設定](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="8aa2b-127">For more information, see [How to: Persist User Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8aa2b-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="8aa2b-128">See Also</span></span>  
 [<span data-ttu-id="8aa2b-129">My.Settings 物件</span><span class="sxs-lookup"><span data-stu-id="8aa2b-129">My.Settings Object</span></span>](../../../../visual-basic/language-reference/objects/my-settings-object.md)  
 [<span data-ttu-id="8aa2b-130">如何：在 Visual Basic 中讀取應用程式設定</span><span class="sxs-lookup"><span data-stu-id="8aa2b-130">How to: Read Application Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)  
 [<span data-ttu-id="8aa2b-131">如何：在 Visual Basic 中變更使用者設定</span><span class="sxs-lookup"><span data-stu-id="8aa2b-131">How to: Change User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)  
 [<span data-ttu-id="8aa2b-132">如何：保存 Visual Basic 中的使用者設定</span><span class="sxs-lookup"><span data-stu-id="8aa2b-132">How to: Persist User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)  
 [<span data-ttu-id="8aa2b-133">管理應用程式設定 (.NET)</span><span class="sxs-lookup"><span data-stu-id="8aa2b-133">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
