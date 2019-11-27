---
title: 使用 My.Resources 及 my.settings 加快開發應用程式的速度
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], developing applications
- rapid application development (RAD), My.Resources
- rapid application development (RAD), My.Settings
- My.Resources object [Visual Basic], developing applications
ms.assetid: 68284ab1-b685-4814-a2a4-01ae40445ff8
ms.openlocfilehash: ce9a5bf76ba3132f58aa40227a145d8b5bf1591d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349270"
---
# <a name="rapid-application-development-with-myresources-and-mysettings-visual-basic"></a><span data-ttu-id="26b72-102">使用 My.Resources 和 My.Settings 進行快速應用程式開發 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="26b72-102">Rapid Application Development with My.Resources and My.Settings (Visual Basic)</span></span>

<span data-ttu-id="26b72-103">`My.Resources` 物件提供應用程式資源的存取權，並可讓您以動態方式取得應用程式的資源。</span><span class="sxs-lookup"><span data-stu-id="26b72-103">The `My.Resources` object provides access to the application's resources and allows you to dynamically retrieve resources for your application.</span></span>  
  
## <a name="retrieving-resources"></a><span data-ttu-id="26b72-104">擷取資源</span><span class="sxs-lookup"><span data-stu-id="26b72-104">Retrieving Resources</span></span>  

 <span data-ttu-id="26b72-105">您可以透過 `My.Resources` 物件來抓取一些資源，例如音訊檔案、圖示、影像和字串。</span><span class="sxs-lookup"><span data-stu-id="26b72-105">A number of resources such as audio files, icons, images, and strings can be retrieved through the `My.Resources` object.</span></span> <span data-ttu-id="26b72-106">例如，您可以存取應用程式的特定文化特性資源檔。</span><span class="sxs-lookup"><span data-stu-id="26b72-106">For example, you can access the application's culture-specific resource files.</span></span> <span data-ttu-id="26b72-107">下列範例會將表單的圖示設定為名為 `Form1Icon` 儲存在應用程式資源檔中的圖示。</span><span class="sxs-lookup"><span data-stu-id="26b72-107">The following example sets the icon of the form to the icon named `Form1Icon` stored in the application's resource file.</span></span>  
  
 [!code-vb[VbVbcnMy#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#7)]  
  
 <span data-ttu-id="26b72-108">`My.Resources` 物件只會公開全域資源。</span><span class="sxs-lookup"><span data-stu-id="26b72-108">The `My.Resources` object exposes only global resources.</span></span> <span data-ttu-id="26b72-109">它不會提供與表單相關聯之資源檔的存取權。</span><span class="sxs-lookup"><span data-stu-id="26b72-109">It does not provide access to resource files associated with forms.</span></span> <span data-ttu-id="26b72-110">您必須從表單存取表單資源。</span><span class="sxs-lookup"><span data-stu-id="26b72-110">You must access the form resources from the form.</span></span>  
  
 <span data-ttu-id="26b72-111">同樣地，`My.Settings` 物件也會提供應用程式設定的存取權，並可讓您動態儲存和抓取應用程式的屬性設定和其他資訊。</span><span class="sxs-lookup"><span data-stu-id="26b72-111">Similarly, the `My.Settings` object provides access to the application's settings and allows you to dynamically store and retrieve property settings and other information for your application.</span></span> <span data-ttu-id="26b72-112">如需詳細資訊，請參閱[My .Resources 物件](../../../visual-basic/language-reference/objects/my-resources-object.md)和[My. Settings 物件](../../../visual-basic/language-reference/objects/my-settings-object.md)。</span><span class="sxs-lookup"><span data-stu-id="26b72-112">For more information, see [My.Resources Object](../../../visual-basic/language-reference/objects/my-resources-object.md) and [My.Settings Object](../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26b72-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="26b72-113">See also</span></span>

- [<span data-ttu-id="26b72-114">My.Resources 物件</span><span class="sxs-lookup"><span data-stu-id="26b72-114">My.Resources Object</span></span>](../../../visual-basic/language-reference/objects/my-resources-object.md)
- [<span data-ttu-id="26b72-115">My.Settings 物件</span><span class="sxs-lookup"><span data-stu-id="26b72-115">My.Settings Object</span></span>](../../../visual-basic/language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="26b72-116">Accessing Application Settings</span><span class="sxs-lookup"><span data-stu-id="26b72-116">Accessing Application Settings</span></span>](../../../visual-basic/developing-apps/programming/app-settings/index.md)
