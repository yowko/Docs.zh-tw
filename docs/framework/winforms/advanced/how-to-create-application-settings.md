---
title: HOW TO：建立應用程式設定
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application settings [Windows Forms], Windows Forms
- application settings [Windows Forms], creating
ms.assetid: 1e7aa347-af75-41e5-89ca-f53cab704f72
ms.openlocfilehash: 5cf109aec8b55650f43f07f5b303c6373df4efc7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59305962"
---
# <a name="how-to-create-application-settings"></a><span data-ttu-id="4a49c-102">HOW TO：建立應用程式設定</span><span class="sxs-lookup"><span data-stu-id="4a49c-102">How to: Create Application Settings</span></span>
<span data-ttu-id="4a49c-103">您可以使用 Managed 程式碼來建立新的應用程式設定，並將設定繫結至表單或表單控制項的屬性，以便在執行階段自動載入及儲存這些設定。</span><span class="sxs-lookup"><span data-stu-id="4a49c-103">Using managed code, you can create new application settings and bind them to properties on your form or your form's controls, so that these settings are loaded and saved automatically at run time.</span></span>  
  
 <span data-ttu-id="4a49c-104">在下列程序中，您將手動建立一個衍生自 <xref:System.Configuration.ApplicationSettingsBase> 的包裝函式類別。</span><span class="sxs-lookup"><span data-stu-id="4a49c-104">In the following procedure, you manually create a wrapper class that derives from <xref:System.Configuration.ApplicationSettingsBase>.</span></span> <span data-ttu-id="4a49c-105">針對這個類別，您會加入可公開存取的屬性，以代表要公開的每一個應用程式設定。</span><span class="sxs-lookup"><span data-stu-id="4a49c-105">To this class you add a publicly accessible property for each application setting that you want to expose.</span></span>  
  
 <span data-ttu-id="4a49c-106">您也可以在 Visual Studio 設計工具中，使用最少的程式碼來執行這個程序。</span><span class="sxs-lookup"><span data-stu-id="4a49c-106">You can also perform this procedure using minimal code in the Visual Studio designer.</span></span>  <span data-ttu-id="4a49c-107">另請參閱[How to:建立使用設計工具的應用程式設定](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/wabtadw6(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="4a49c-107">Also see [How to: Create Application Settings Using the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/wabtadw6(v=vs.100)).</span></span>  
  
### <a name="to-create-new-application-settings-programmatically"></a><span data-ttu-id="4a49c-108">以程式設計方式建立新的應用程式設定</span><span class="sxs-lookup"><span data-stu-id="4a49c-108">To create new Application Settings programmatically</span></span>  
  
1. <span data-ttu-id="4a49c-109">將新類別加入您的專案中，並且重新命名。</span><span class="sxs-lookup"><span data-stu-id="4a49c-109">Add a new class to your project, and rename it.</span></span> <span data-ttu-id="4a49c-110">此程序中，我們會呼叫這個類別`MyUserSettings`。</span><span class="sxs-lookup"><span data-stu-id="4a49c-110">For this procedure, we will call this class `MyUserSettings`.</span></span> <span data-ttu-id="4a49c-111">變更類別定義，使該類別衍生自 <xref:System.Configuration.ApplicationSettingsBase>。</span><span class="sxs-lookup"><span data-stu-id="4a49c-111">Change the class definition so that the class derives from <xref:System.Configuration.ApplicationSettingsBase>.</span></span>  
  
2. <span data-ttu-id="4a49c-112">在包裝函式類別上為每一個所需的應用程式設定定義屬性，並且依據設定的範圍使用 <xref:System.Configuration.ApplicationScopedSettingAttribute> 或 <xref:System.Configuration.UserScopedSettingAttribute> 來套用該屬性。</span><span class="sxs-lookup"><span data-stu-id="4a49c-112">Define a property on this wrapper class for each application setting you require, and apply that property with either the <xref:System.Configuration.ApplicationScopedSettingAttribute> or <xref:System.Configuration.UserScopedSettingAttribute>, depending on the scope of the setting.</span></span> <span data-ttu-id="4a49c-113">如需有關設定範圍的詳細資訊，請參閱 <<c0> [ 應用程式設定概觀](application-settings-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="4a49c-113">For more information about settings scope, see [Application Settings Overview](application-settings-overview.md).</span></span> <span data-ttu-id="4a49c-114">現在，您的程式碼應該如下所示：</span><span class="sxs-lookup"><span data-stu-id="4a49c-114">By now, your code should look like this:</span></span>  
  
     [!code-csharp[ApplicationSettings.Create#1](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/MyAppSettings.cs#1)]
     [!code-vb[ApplicationSettings.Create#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/MyAppSettings.vb#1)]  
  
3. <span data-ttu-id="4a49c-115">在應用程式中建立這個包裝函式類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="4a49c-115">Create an instance of this wrapper class in your application.</span></span> <span data-ttu-id="4a49c-116">這個執行個體通常會是主要表單的私用成員。</span><span class="sxs-lookup"><span data-stu-id="4a49c-116">It will commonly be a private member of the main form.</span></span> <span data-ttu-id="4a49c-117">定義類別之後，您需要將類別繫結至屬性；在本例中，即為表單的 <xref:System.Windows.Forms.Form.BackColor%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="4a49c-117">Now that you have defined your class, you need to bind it to a property; in this case, the <xref:System.Windows.Forms.Form.BackColor%2A> property of your form.</span></span> <span data-ttu-id="4a49c-118">您可以在您的表單來完成`Load`事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="4a49c-118">You can accomplish this in your form's `Load` event handler.</span></span>  
  
     [!code-csharp[ApplicationSettings.Create#2](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/Form1.cs#2)]
     [!code-vb[ApplicationSettings.Create#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/Form1.vb#2)]  
  
4. <span data-ttu-id="4a49c-119">如果您提供在執行階段變更設定的方式，則需要在關閉表單時將使用者的目前設定儲存至磁碟，否則這些變更將會遺失。</span><span class="sxs-lookup"><span data-stu-id="4a49c-119">If you provide a way to change settings at run time, you will need to save the user's current settings to disk when your form closes, or else these changes will be lost.</span></span>  
  
     [!code-csharp[ApplicationSettings.Create#3](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/Form1.cs#3)]
     [!code-vb[ApplicationSettings.Create#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/Form1.vb#3)]  
  
     <span data-ttu-id="4a49c-120">您現在已成功建立新的應用程式設定，並將設定繫結至指定的屬性。</span><span class="sxs-lookup"><span data-stu-id="4a49c-120">You have now successfully created a new application setting and bound it to the specified property.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="4a49c-121">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="4a49c-121">.NET Framework Security</span></span>  
 <span data-ttu-id="4a49c-122">預設的設定提供者 <xref:System.Configuration.LocalFileSettingsProvider> 將資訊以純文字格式保存於組態檔。</span><span class="sxs-lookup"><span data-stu-id="4a49c-122">The default settings provider, <xref:System.Configuration.LocalFileSettingsProvider>, persists information to configuration files as plain text.</span></span> <span data-ttu-id="4a49c-123">這會將安全性限定為目前使用者之作業系統所提供的檔案存取安全性。</span><span class="sxs-lookup"><span data-stu-id="4a49c-123">This limits security to the file access security provided by the operating system for the current user.</span></span> <span data-ttu-id="4a49c-124">因此，您必須小心使用儲存在組態檔中的資訊。</span><span class="sxs-lookup"><span data-stu-id="4a49c-124">Because of this, care must be taken with the information stored in configuration files.</span></span> <span data-ttu-id="4a49c-125">例如，應用程式設定的常見用途之一，是儲存指向應用程式資料存放區的連接字串。</span><span class="sxs-lookup"><span data-stu-id="4a49c-125">For example, one common use for application settings is to store connection strings that point to the application's data store.</span></span> <span data-ttu-id="4a49c-126">不過，基於安全性考量，這類字串不應包含密碼。</span><span class="sxs-lookup"><span data-stu-id="4a49c-126">However, because of security concerns, such strings should not include passwords.</span></span> <span data-ttu-id="4a49c-127">如需連接字串的詳細資訊，請參閱 <xref:System.Configuration.SpecialSetting>。</span><span class="sxs-lookup"><span data-stu-id="4a49c-127">For more information about connection strings, see <xref:System.Configuration.SpecialSetting>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a49c-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4a49c-128">See also</span></span>

- <xref:System.Configuration.SpecialSettingAttribute>
- <xref:System.Configuration.LocalFileSettingsProvider>
- [<span data-ttu-id="4a49c-129">應用程式設定概觀</span><span class="sxs-lookup"><span data-stu-id="4a49c-129">Application Settings Overview</span></span>](application-settings-overview.md)
- [<span data-ttu-id="4a49c-130">如何：驗證應用程式設定</span><span class="sxs-lookup"><span data-stu-id="4a49c-130">How to: Validate Application Settings</span></span>](how-to-validate-application-settings.md)
