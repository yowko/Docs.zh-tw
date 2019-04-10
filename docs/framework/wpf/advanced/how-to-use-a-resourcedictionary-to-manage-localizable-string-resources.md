---
title: HOW TO：使用 ResourceDictionary 管理可當地語系化的字串資源
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- resources [WPF], packaging string resources
- packaging string resources [WPF]
- ResourceDictionary [WPF]
- localization [WPF], packaging string resources
ms.assetid: 19e7d9a5-20df-4ad3-b157-fe6515902e5e
ms.openlocfilehash: b56a307ed31fc8f7573215eac70350ac5e4b9de1
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59311314"
---
# <a name="how-to-use-a-resourcedictionary-to-manage-localizable-string-resources"></a><span data-ttu-id="f9619-102">HOW TO：使用 ResourceDictionary 管理可當地語系化的字串資源</span><span class="sxs-lookup"><span data-stu-id="f9619-102">How to: Use a ResourceDictionary to Manage Localizable String Resources</span></span>
<span data-ttu-id="f9619-103">此範例示範如何使用<xref:System.Windows.ResourceDictionary>Windows Presentation Foundation (WPF) 應用程式的套件可當地語系化的字串資源。</span><span class="sxs-lookup"><span data-stu-id="f9619-103">This example shows how to use a <xref:System.Windows.ResourceDictionary> to package localizable string resources for Windows Presentation Foundation (WPF) applications.</span></span>  
  
### <a name="to-use-a-resourcedictionary-to-manage-localizable-string-resources"></a><span data-ttu-id="f9619-104">若要使用 ResourceDictionary 管理可當地語系化的字串資源</span><span class="sxs-lookup"><span data-stu-id="f9619-104">To use a ResourceDictionary to manage localizable string resources</span></span>  
  
1. <span data-ttu-id="f9619-105">建立<xref:System.Windows.ResourceDictionary>，其中包含您想要當地語系化的字串。</span><span class="sxs-lookup"><span data-stu-id="f9619-105">Create a <xref:System.Windows.ResourceDictionary> that contains the strings you would like to localize.</span></span> <span data-ttu-id="f9619-106">下列程式碼示範範例。</span><span class="sxs-lookup"><span data-stu-id="f9619-106">The following code shows an example.</span></span>  
  
     [!code-xaml[StringLocalizationSample#StringResourceDictionary](~/samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/StringResources.xaml#stringresourcedictionary)]  
  
     <span data-ttu-id="f9619-107">此程式碼定義之字串資源`localizedMessage`，型別的<xref:System.String>，從<xref:System>mscorlib.dll 中的命名空間。</span><span class="sxs-lookup"><span data-stu-id="f9619-107">This code defines a string resource, `localizedMessage`, of type <xref:System.String>, from the <xref:System> namespace in mscorlib.dll.</span></span>  
  
2. <span data-ttu-id="f9619-108">新增<xref:System.Windows.ResourceDictionary>應用程式時，使用下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="f9619-108">Add the <xref:System.Windows.ResourceDictionary> to your application, using the following code.</span></span>  
  
     [!code-xaml[StringLocalizationSample#ReferencingStringResourceDictionary](~/samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/App.xaml#referencingstringresourcedictionary)]  
  
3. <span data-ttu-id="f9619-109">使用來自標記的字串資源使用[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]如下所示。</span><span class="sxs-lookup"><span data-stu-id="f9619-109">Use the string resource from markup, using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] like the following.</span></span>  
  
     [!code-xaml[StringLocalizationSample#GetLocalizedResourceFromMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/MainWindow.xaml#getlocalizedresourcefrommarkup)]  
  
4. <span data-ttu-id="f9619-110">使用類似下列程式碼，即可利用來自程式碼後置的字串資源。</span><span class="sxs-lookup"><span data-stu-id="f9619-110">Use the string resource from code-behind, using code like the following.</span></span>  
  
     [!code-csharp[StringLocalizationSample#GetLocalizedResourceFromCode](~/samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/MainWindow.xaml.cs#getlocalizedresourcefromcode)]
     [!code-vb[StringLocalizationSample#GetLocalizedResourceFromCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StringLocalizationSample/VisualBasic/MainWindow.xaml.vb#getlocalizedresourcefromcode)]  
  
5. <span data-ttu-id="f9619-111">將應用程式當地語系化。</span><span class="sxs-lookup"><span data-stu-id="f9619-111">Localize the application.</span></span> <span data-ttu-id="f9619-112">如需詳細資訊，請參閱 <<c0> [ 將應用程式當地語系化](how-to-localize-an-application.md)。</span><span class="sxs-lookup"><span data-stu-id="f9619-112">For more information, see [Localize an Application](how-to-localize-an-application.md).</span></span>
