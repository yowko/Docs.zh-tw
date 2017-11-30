---
title: "當地語系化"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- culture, localization
- application development [.NET Framework], localization
- globalization [.NET Framework], localization
- code blocks
- international applications [.NET Framework], localization
- global applications, localization
- world-ready applications, localization
- user interface blocks
- localization [.NET Framework], about localization
- localizing resources
ms.assetid: 49d520d7-92d7-44ee-bb24-8b615db1d41b
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4aaf2da77a1fab55cbebd6bfa05a2b1c74e5cbbd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="localization"></a><span data-ttu-id="174c8-102">當地語系化</span><span class="sxs-lookup"><span data-stu-id="174c8-102">Localization</span></span>
<span data-ttu-id="174c8-103">當地語系化是轉譯為每個應用程式將支援的文化特性的當地語系化版本的應用程式資源的程序。</span><span class="sxs-lookup"><span data-stu-id="174c8-103">Localization is the process of translating an application's resources into localized versions for each culture that the application will support.</span></span> <span data-ttu-id="174c8-104">您應該完成後才繼續進行當地語系化步驟[當地語系化能力審查](../../../docs/standard/globalization-localization/localizability-review.md)步驟，以確認全球化應用程式已準備好進行當地語系化。</span><span class="sxs-lookup"><span data-stu-id="174c8-104">You should proceed to the localization step only after completing the [Localizability Review](../../../docs/standard/globalization-localization/localizability-review.md) step to verify that the globalized application is ready for localization.</span></span>  
  
 <span data-ttu-id="174c8-105">準備好進行當地語系化的應用程式分成兩個區塊的區塊，其中包含所有的使用者介面項目，包含可執行程式碼的區塊。</span><span class="sxs-lookup"><span data-stu-id="174c8-105">An application that is ready for localization is separated into two conceptual blocks, a block that contains all user interface elements and a block that contains executable code.</span></span> <span data-ttu-id="174c8-106">使用者介面區塊包含只可當地語系化的使用者介面元素，例如字串、 錯誤訊息、 對話方塊、 功能表、 內嵌的物件，依此類推中性文化特性的資源。</span><span class="sxs-lookup"><span data-stu-id="174c8-106">The user interface block contains only localizable user-interface elements such as strings, error messages, dialog boxes, menus, embedded object resources, and so on for the neutral culture.</span></span> <span data-ttu-id="174c8-107">程式碼區塊包含只可供所有支援的文化特性的應用程式程式碼。</span><span class="sxs-lookup"><span data-stu-id="174c8-107">The code block contains only the application code to be used by all supported cultures.</span></span> <span data-ttu-id="174c8-108">通用語言執行平台支援將應用程式的可執行程式碼和其資源的附屬組件資源模型。</span><span class="sxs-lookup"><span data-stu-id="174c8-108">The common language runtime supports a satellite assembly resource model that separates an application's executable code from its resources.</span></span> <span data-ttu-id="174c8-109">如需實作此模型的詳細資訊，請參閱[桌面應用程式中的資源](../../../docs/framework/resources/index.md)。</span><span class="sxs-lookup"><span data-stu-id="174c8-109">For more information about implementing this model, see [Resources in Desktop Apps](../../../docs/framework/resources/index.md).</span></span>  
  
 <span data-ttu-id="174c8-110">每個當地語系化版本的應用程式，加入新的附屬組件，其中包含轉譯成適當的語言為目標的文化特性的當地語系化的使用者介面區塊。</span><span class="sxs-lookup"><span data-stu-id="174c8-110">For each localized version of your application, add a new satellite assembly that contains the localized user interface block translated into the appropriate language for the target culture.</span></span> <span data-ttu-id="174c8-111">所有文化特性的程式碼區塊應該維持不變。</span><span class="sxs-lookup"><span data-stu-id="174c8-111">The code block for all cultures should remain the same.</span></span> <span data-ttu-id="174c8-112">使用者介面區塊的程式碼區塊的當地語系化版本的組合會產生您的應用程式的當地語系化的版本。</span><span class="sxs-lookup"><span data-stu-id="174c8-112">The combination of a localized version of the user interface block with the code block produces a localized version of your application.</span></span>  
  
 <span data-ttu-id="174c8-113">[!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)]提供 Windows Form 資源編輯器 (Winres.exe)，可讓您快速將 Windows Form 當地語系化目標文化特性。</span><span class="sxs-lookup"><span data-stu-id="174c8-113">The [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] supplies the Windows Forms Resource Editor (Winres.exe) that allows you to quickly localize Windows Forms for target cultures.</span></span> <span data-ttu-id="174c8-114">使用此工具的相關資訊，請參閱[Winres.exe （Windows Form 資源編輯器）](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="174c8-114">For information about using this tool, see [Winres.exe (Windows Forms Resource Editor)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="174c8-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="174c8-115">See Also</span></span>  
 [<span data-ttu-id="174c8-116">全球化和當地語系化</span><span class="sxs-lookup"><span data-stu-id="174c8-116">Globalization and Localization</span></span>](../../../docs/standard/globalization-localization/index.md)  
 [<span data-ttu-id="174c8-117">可當地語系化檢閱</span><span class="sxs-lookup"><span data-stu-id="174c8-117">Localizability Review</span></span>](../../../docs/standard/globalization-localization/localizability-review.md)  
 [<span data-ttu-id="174c8-118">全球化</span><span class="sxs-lookup"><span data-stu-id="174c8-118">Globalization</span></span>](../../../docs/standard/globalization-localization/globalization.md)  
 [<span data-ttu-id="174c8-119">桌面應用程式中的資源</span><span class="sxs-lookup"><span data-stu-id="174c8-119">Resources in Desktop Apps</span></span>](../../../docs/framework/resources/index.md)
