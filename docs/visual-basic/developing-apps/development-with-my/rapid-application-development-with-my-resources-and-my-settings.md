---
title: "使用 My.Resources 和 My.Settings 進行快速應用程式開發 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My.Settings object [Visual Basic], developing applications
- rapid application development (RAD), My.Resources
- rapid application development (RAD), My.Settings
- My.Resources object [Visual Basic], developing applications
ms.assetid: 68284ab1-b685-4814-a2a4-01ae40445ff8
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1657febf935560ff4c8dd2f54b10fdcb2254891f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="rapid-application-development-with-myresources-and-mysettings-visual-basic"></a><span data-ttu-id="46fbf-102">使用 My.Resources 和 My.Settings 進行快速應用程式開發 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="46fbf-102">Rapid Application Development with My.Resources and My.Settings (Visual Basic)</span></span>
<span data-ttu-id="46fbf-103">`My.Resources`物件提供的應用程式資源的存取權，並可讓您以動態方式擷取您的應用程式的資源。</span><span class="sxs-lookup"><span data-stu-id="46fbf-103">The `My.Resources` object provides access to the application's resources and allows you to dynamically retrieve resources for your application.</span></span>  
  
## <a name="retrieving-resources"></a><span data-ttu-id="46fbf-104">擷取資源</span><span class="sxs-lookup"><span data-stu-id="46fbf-104">Retrieving Resources</span></span>  
 <span data-ttu-id="46fbf-105">可以透過擷取的資源，例如音訊檔案、 圖示、 影像和字串的數字`My.Resources`物件。</span><span class="sxs-lookup"><span data-stu-id="46fbf-105">A number of resources such as audio files, icons, images, and strings can be retrieved through the `My.Resources` object.</span></span> <span data-ttu-id="46fbf-106">例如，您可以存取應用程式的特定文化特性資源檔。</span><span class="sxs-lookup"><span data-stu-id="46fbf-106">For example, you can access the application's culture-specific resource files.</span></span> <span data-ttu-id="46fbf-107">下列範例會設定表單的圖示的圖示，名為`Form1Icon`儲存應用程式的資源檔案。</span><span class="sxs-lookup"><span data-stu-id="46fbf-107">The following example sets the icon of the form to the icon named `Form1Icon` stored in the application's resource file.</span></span>  
  
 [!code-vb[VbVbcnMy#7](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/rapid-application-development-with-my-resources-and-my-settings_1.vb)]  
  
 <span data-ttu-id="46fbf-108">`My.Resources`物件會公開只有全域資源。</span><span class="sxs-lookup"><span data-stu-id="46fbf-108">The `My.Resources` object exposes only global resources.</span></span> <span data-ttu-id="46fbf-109">它不提供與表單相關聯的資源檔案的存取權。</span><span class="sxs-lookup"><span data-stu-id="46fbf-109">It does not provide access to resource files associated with forms.</span></span> <span data-ttu-id="46fbf-110">您必須在表單中存取的表單資源。</span><span class="sxs-lookup"><span data-stu-id="46fbf-110">You must access the form resources from the form.</span></span> <span data-ttu-id="46fbf-111">如需詳細資訊，請參閱[逐步解說：將 Windows Forms 當地語系化](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5)。</span><span class="sxs-lookup"><span data-stu-id="46fbf-111">For more information, see [Walkthrough: Localizing Windows Forms](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5).</span></span>  
  
 <span data-ttu-id="46fbf-112">同樣地，`My.Settings`物件存取應用程式的設定，並可讓您動態儲存及擷取屬性設定和應用程式的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="46fbf-112">Similarly, the `My.Settings` object provides access to the application's settings and allows you to dynamically store and retrieve property settings and other information for your application.</span></span> <span data-ttu-id="46fbf-113">如需詳細資訊，請參閱[My.Resources 物件](../../../visual-basic/language-reference/objects/my-resources-object.md)和[My.Settings 物件](../../../visual-basic/language-reference/objects/my-settings-object.md)。</span><span class="sxs-lookup"><span data-stu-id="46fbf-113">For more information, see [My.Resources Object](../../../visual-basic/language-reference/objects/my-resources-object.md) and [My.Settings Object](../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46fbf-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="46fbf-114">See Also</span></span>  
 [<span data-ttu-id="46fbf-115">My.Resources 物件</span><span class="sxs-lookup"><span data-stu-id="46fbf-115">My.Resources Object</span></span>](../../../visual-basic/language-reference/objects/my-resources-object.md)  
 [<span data-ttu-id="46fbf-116">My.Settings 物件</span><span class="sxs-lookup"><span data-stu-id="46fbf-116">My.Settings Object</span></span>](../../../visual-basic/language-reference/objects/my-settings-object.md)  
 [<span data-ttu-id="46fbf-117">存取應用程式設定</span><span class="sxs-lookup"><span data-stu-id="46fbf-117">Accessing Application Settings</span></span>](../../../visual-basic/developing-apps/programming/app-settings/accessing-application-settings.md)
