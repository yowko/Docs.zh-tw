---
title: HOW TO：在可當地語系化的應用程式中使用資源
ms.date: 03/30/2017
helpviewer_keywords:
- applications [WPF], localizable
- localizable applications [WPF]
ms.assetid: 08539ad6-7fca-4f34-b82b-ff439e11dfa7
ms.openlocfilehash: ad257e7703bcee8f71da78ad5928d7999365c38f
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57376153"
---
# <a name="how-to-use-resources-in-localizable-applications"></a><span data-ttu-id="7ff4b-102">HOW TO：在可當地語系化的應用程式中使用資源</span><span class="sxs-lookup"><span data-stu-id="7ff4b-102">How to: Use Resources in Localizable Applications</span></span>
<span data-ttu-id="7ff4b-103">當地語系化表示適應[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]不同文化特性。</span><span class="sxs-lookup"><span data-stu-id="7ff4b-103">Localization means to adapt a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] to different cultures.</span></span> <span data-ttu-id="7ff4b-104">若要執行這項操作，必須翻譯標題、說明文字、清單方塊項目等文字。</span><span class="sxs-lookup"><span data-stu-id="7ff4b-104">To do this, text such as titles, captions, list box items and so forth have to be translated.</span></span> <span data-ttu-id="7ff4b-105">為了簡化翻譯過程，會將要翻譯的項目收集到資源檔中。</span><span class="sxs-lookup"><span data-stu-id="7ff4b-105">To make translation easier the items to be translated are collected into resource files.</span></span> <span data-ttu-id="7ff4b-106">請參閱[將應用程式當地語系化](how-to-localize-an-application.md)如需如何建立當地語系化的資源檔的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="7ff4b-106">See [Localize an Application](how-to-localize-an-application.md) for information on how to create a resource file for localization.</span></span> <span data-ttu-id="7ff4b-107">若要讓[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式當地語系化，開發人員建置成資源組件的所有可當地語系化的資源。</span><span class="sxs-lookup"><span data-stu-id="7ff4b-107">To make a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application localizable, developers need to build all the localizable resources into a resource assembly.</span></span> <span data-ttu-id="7ff4b-108">資源組件已當地語系化成不同的語言和程式碼後置使用資源管理[!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)]載入。</span><span class="sxs-lookup"><span data-stu-id="7ff4b-108">The resource assembly is localized into different languages, and the code-behind uses resource management [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] to load.</span></span> <span data-ttu-id="7ff4b-109">其中一個所需的檔案[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式是專案檔 (.proj)。</span><span class="sxs-lookup"><span data-stu-id="7ff4b-109">One of the files required for a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application is a project file (.proj).</span></span> <span data-ttu-id="7ff4b-110">專案檔案應該包含您在應用程式中使用的所有資源。</span><span class="sxs-lookup"><span data-stu-id="7ff4b-110">All resources that you use in your application should be included in the project file.</span></span> <span data-ttu-id="7ff4b-111">下列程式碼範例會顯示這點。</span><span class="sxs-lookup"><span data-stu-id="7ff4b-111">The following code example shows this.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7ff4b-112">範例</span><span class="sxs-lookup"><span data-stu-id="7ff4b-112">Example</span></span>  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]  
  
 `<Resource Include="data\picture1.jpg"/>`  
  
 `<EmbeddedResource Include="data\stringtable.en-US.restext"/>`  
  
 <span data-ttu-id="7ff4b-113">若要在您的應用程式中使用資源，您具現化<xref:System.Resources.ResourceManager>並載入您想要使用的資源。</span><span class="sxs-lookup"><span data-stu-id="7ff4b-113">To use a resource in your application, you instantiate <xref:System.Resources.ResourceManager> and load the resource you want to use.</span></span> <span data-ttu-id="7ff4b-114">以下示範如何執行這項操作。</span><span class="sxs-lookup"><span data-stu-id="7ff4b-114">The following demonstrates how to do this.</span></span>  
  
 [!code-csharp[LocalizationResources#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]
