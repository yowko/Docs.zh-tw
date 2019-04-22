---
title: HOW TO：保存 Visual Basic 中的使用者設定
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], persisting user settings
- persistence [Visual Basic], persisting user settings [Visual Basic]
- user settings [Visual Basic], persisting
ms.assetid: 0e5e6415-b6e2-4602-9be0-a65fa167d007
ms.openlocfilehash: 35997db52a59aeaff5a2c404ea83b15639ea23a0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58825177"
---
# <a name="how-to-persist-user-settings-in-visual-basic"></a><span data-ttu-id="a8066-102">HOW TO：保存 Visual Basic 中的使用者設定</span><span class="sxs-lookup"><span data-stu-id="a8066-102">How to: Persist User Settings in Visual Basic</span></span>
<span data-ttu-id="a8066-103">您可以使用 `My.Settings.Save` 方法來保存使用者設定的變更。</span><span class="sxs-lookup"><span data-stu-id="a8066-103">You can use the `My.Settings.Save` method to persist changes to the user settings.</span></span>  
  
 <span data-ttu-id="a8066-104">通常，應用程式設計成在關閉應用程式時，保存使用者設定的變更。</span><span class="sxs-lookup"><span data-stu-id="a8066-104">Typically, applications are designed to persist the changes to the user settings when the application shuts down.</span></span> <span data-ttu-id="a8066-105">這是因為儲存變更可能需要幾秒鐘的時間，視幾個因素而定。</span><span class="sxs-lookup"><span data-stu-id="a8066-105">This is because saving the settings can take, depending on several factors, several seconds.</span></span>  
  
 <span data-ttu-id="a8066-106">如需詳細資訊，請參閱 [My.Settings 物件](../../../../visual-basic/language-reference/objects/my-settings-object.md)。</span><span class="sxs-lookup"><span data-stu-id="a8066-106">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a8066-107">雖然您可以在執行階段變更和儲存使用者範圍設定的值，但是應用程式範圍的設定為唯讀，且無法以程式設計方式變更。</span><span class="sxs-lookup"><span data-stu-id="a8066-107">Although you can change and save the values of user-scope settings at run time, application-scope settings are read-only and cannot be changed programmatically.</span></span> <span data-ttu-id="a8066-108">建立應用程式時，您可以透過 [專案設計工具]，或藉由編輯應用程式的組態檔，來變更應用程式範圍的設定。</span><span class="sxs-lookup"><span data-stu-id="a8066-108">You can change application-scope settings when creating the application, through the **Project Designer**, or by editing the application's configuration file.</span></span> <span data-ttu-id="a8066-109">如需詳細資訊，請參閱[管理應用程式設定 (.NET)](/visualstudio/ide/managing-application-settings-dotnet)。</span><span class="sxs-lookup"><span data-stu-id="a8066-109">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8066-110">範例</span><span class="sxs-lookup"><span data-stu-id="a8066-110">Example</span></span>  
 <span data-ttu-id="a8066-111">此範例會變更 `LastChanged` 使用者設定的值，然後呼叫 `My.Settings.Save` 方法儲存該變更。</span><span class="sxs-lookup"><span data-stu-id="a8066-111">This example changes the value of the `LastChanged` user setting and saves that change by calling the `My.Settings.Save` method.</span></span>  
  
 [!code-vb[VbVbalrMyResources#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#5)]  
  
 <span data-ttu-id="a8066-112">為了確保此範例正常運作，您的應用程式必須具有 `Date` 類型的 `LastChanged` 使用者設定。</span><span class="sxs-lookup"><span data-stu-id="a8066-112">For this example to work, your application must have a `LastChanged` user setting, of type `Date`.</span></span> <span data-ttu-id="a8066-113">如需詳細資訊，請參閱[管理應用程式設定 (.NET)](/visualstudio/ide/managing-application-settings-dotnet)。</span><span class="sxs-lookup"><span data-stu-id="a8066-113">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8066-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a8066-114">See also</span></span>

- [<span data-ttu-id="a8066-115">My.Settings 物件</span><span class="sxs-lookup"><span data-stu-id="a8066-115">My.Settings Object</span></span>](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="a8066-116">如何：在 Visual Basic 中讀取應用程式設定</span><span class="sxs-lookup"><span data-stu-id="a8066-116">How to: Read Application Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [<span data-ttu-id="a8066-117">如何：在 Visual Basic 中變更使用者設定</span><span class="sxs-lookup"><span data-stu-id="a8066-117">How to: Change User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [<span data-ttu-id="a8066-118">如何：在 Visual Basic 中建立使用者設定的屬性方格</span><span class="sxs-lookup"><span data-stu-id="a8066-118">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="a8066-119">管理應用程式設定 (.NET)</span><span class="sxs-lookup"><span data-stu-id="a8066-119">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
