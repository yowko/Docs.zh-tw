---
title: 使用 My.Resources 及 my.settings 加快開發應用程式的速度
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], developing applications
- rapid application development (RAD), My.Resources
- rapid application development (RAD), My.Settings
- My.Resources object [Visual Basic], developing applications
ms.assetid: 68284ab1-b685-4814-a2a4-01ae40445ff8
ms.openlocfilehash: 6c53d11a3830a5a8a2cb898728bed8694a226686
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411664"
---
# <a name="rapid-application-development-with-myresources-and-mysettings-visual-basic"></a><span data-ttu-id="cd145-102">使用 My.Resources 和 My.Settings 進行快速應用程式開發 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd145-102">Rapid Application Development with My.Resources and My.Settings (Visual Basic)</span></span>

<span data-ttu-id="cd145-103">`My.Resources`物件提供應用程式資源的存取權，並可讓您以動態方式取得應用程式的資源。</span><span class="sxs-lookup"><span data-stu-id="cd145-103">The `My.Resources` object provides access to the application's resources and allows you to dynamically retrieve resources for your application.</span></span>  
  
## <a name="retrieving-resources"></a><span data-ttu-id="cd145-104">擷取資源</span><span class="sxs-lookup"><span data-stu-id="cd145-104">Retrieving Resources</span></span>  

 <span data-ttu-id="cd145-105">您可以透過物件來抓取一些資源，例如音訊檔案、圖示、影像和字串 `My.Resources` 。</span><span class="sxs-lookup"><span data-stu-id="cd145-105">A number of resources such as audio files, icons, images, and strings can be retrieved through the `My.Resources` object.</span></span> <span data-ttu-id="cd145-106">例如，您可以存取應用程式的特定文化特性資源檔。</span><span class="sxs-lookup"><span data-stu-id="cd145-106">For example, you can access the application's culture-specific resource files.</span></span> <span data-ttu-id="cd145-107">下列範例會將表單的圖示設定為 `Form1Icon` 應用程式資源檔中所儲存的圖示。</span><span class="sxs-lookup"><span data-stu-id="cd145-107">The following example sets the icon of the form to the icon named `Form1Icon` stored in the application's resource file.</span></span>  
  
 [!code-vb[VbVbcnMy#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#7)]  
  
 <span data-ttu-id="cd145-108">`My.Resources`物件只會公開全域資源。</span><span class="sxs-lookup"><span data-stu-id="cd145-108">The `My.Resources` object exposes only global resources.</span></span> <span data-ttu-id="cd145-109">它不會提供與表單相關聯之資源檔的存取權。</span><span class="sxs-lookup"><span data-stu-id="cd145-109">It does not provide access to resource files associated with forms.</span></span> <span data-ttu-id="cd145-110">您必須從表單存取表單資源。</span><span class="sxs-lookup"><span data-stu-id="cd145-110">You must access the form resources from the form.</span></span>  
  
 <span data-ttu-id="cd145-111">同樣地， `My.Settings` 物件也會提供應用程式設定的存取權，並可讓您動態儲存和抓取應用程式的屬性設定和其他資訊。</span><span class="sxs-lookup"><span data-stu-id="cd145-111">Similarly, the `My.Settings` object provides access to the application's settings and allows you to dynamically store and retrieve property settings and other information for your application.</span></span> <span data-ttu-id="cd145-112">如需詳細資訊，請參閱[My .Resources 物件](../../language-reference/objects/my-resources-object.md)和[My. Settings 物件](../../language-reference/objects/my-settings-object.md)。</span><span class="sxs-lookup"><span data-stu-id="cd145-112">For more information, see [My.Resources Object](../../language-reference/objects/my-resources-object.md) and [My.Settings Object](../../language-reference/objects/my-settings-object.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd145-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd145-113">See also</span></span>

- [<span data-ttu-id="cd145-114">My.Resources 物件</span><span class="sxs-lookup"><span data-stu-id="cd145-114">My.Resources Object</span></span>](../../language-reference/objects/my-resources-object.md)
- [<span data-ttu-id="cd145-115">My.Settings 物件</span><span class="sxs-lookup"><span data-stu-id="cd145-115">My.Settings Object</span></span>](../../language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="cd145-116">Accessing Application Settings</span><span class="sxs-lookup"><span data-stu-id="cd145-116">Accessing Application Settings</span></span>](../programming/app-settings/index.md)
