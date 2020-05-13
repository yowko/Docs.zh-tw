---
title: 如何：在可當地語系化的應用程式中使用資源
ms.date: 03/30/2017
helpviewer_keywords:
- applications [WPF], localizable
- localizable applications [WPF]
ms.assetid: 08539ad6-7fca-4f34-b82b-ff439e11dfa7
ms.openlocfilehash: 8f516a86036656b98add23d38c588b5c19be4d7a
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212471"
---
# <a name="how-to-use-resources-in-localizable-apps"></a><span data-ttu-id="d386e-102">如何：在可當地語系化的應用程式中使用資源</span><span class="sxs-lookup"><span data-stu-id="d386e-102">How to: Use resources in localizable apps</span></span>

<span data-ttu-id="d386e-103">當地語系化是指將使用者介面調整成不同的文化特性。</span><span class="sxs-lookup"><span data-stu-id="d386e-103">Localization means to adapt a user interface to different cultures.</span></span> <span data-ttu-id="d386e-104">若要這樣做，您必須翻譯標題、標題和清單方塊專案等文字。</span><span class="sxs-lookup"><span data-stu-id="d386e-104">To do this, text such as titles, captions, and list box items must be translated.</span></span> <span data-ttu-id="d386e-105">為了讓翻譯變得更容易，要轉譯的專案會收集到資源檔中。</span><span class="sxs-lookup"><span data-stu-id="d386e-105">To make translation easier, the items to be translated are collected into resource files.</span></span> <span data-ttu-id="d386e-106">如需如何建立資源檔以進行當地語系化的詳細資訊，請參閱[當地語系化應用程式](how-to-localize-an-application.md)。</span><span class="sxs-lookup"><span data-stu-id="d386e-106">See [Localize an app](how-to-localize-an-application.md) for information on how to create a resource file for localization.</span></span> <span data-ttu-id="d386e-107">若要讓 WPF 應用程式當地語系化，開發人員需要將所有可當地語系化的資源建立到資源元件中。</span><span class="sxs-lookup"><span data-stu-id="d386e-107">To make a WPF application localizable, developers need to build all the localizable resources into a resource assembly.</span></span> <span data-ttu-id="d386e-108">資源元件已當地語系化成不同的語言，而程式碼後置使用資源管理 API 來載入。</span><span class="sxs-lookup"><span data-stu-id="d386e-108">The resource assembly is localized into different languages, and the code-behind uses resource management API to load.</span></span>

## <a name="example"></a><span data-ttu-id="d386e-109">範例</span><span class="sxs-lookup"><span data-stu-id="d386e-109">Example</span></span>

<span data-ttu-id="d386e-110">WPF 應用程式所需的其中一個檔案是專案檔（proj）。</span><span class="sxs-lookup"><span data-stu-id="d386e-110">One of the files required for a WPF application is a project file (.proj).</span></span> <span data-ttu-id="d386e-111">專案檔案應該包含您在應用程式中使用的所有資源。</span><span class="sxs-lookup"><span data-stu-id="d386e-111">All resources that you use in your application should be included in the project file.</span></span> <span data-ttu-id="d386e-112">下列 XAML 範例顯示這種情況。</span><span class="sxs-lookup"><span data-stu-id="d386e-112">The following XAML example shows this.</span></span>

```xaml
<Resource Include="data\picture1.jpg"/>  
<EmbeddedResource Include="data\stringtable.en-US.restext"/>
```

<span data-ttu-id="d386e-113">若要在您的應用程式中使用資源，請具現化 <xref:System.Resources.ResourceManager> 並載入您要使用的資源。</span><span class="sxs-lookup"><span data-stu-id="d386e-113">To use a resource in your application, instantiate <xref:System.Resources.ResourceManager> and load the resource you want to use.</span></span> <span data-ttu-id="d386e-114">下列 c # 程式碼示範如何執行這項操作。</span><span class="sxs-lookup"><span data-stu-id="d386e-114">The following C# code demonstrates how to do this.</span></span>

[!code-csharp[LocalizationResources#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]

## <a name="see-also"></a><span data-ttu-id="d386e-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="d386e-115">See also</span></span>

- [<span data-ttu-id="d386e-116">將應用程式當地語系化</span><span class="sxs-lookup"><span data-stu-id="d386e-116">Localize an app</span></span>](how-to-localize-an-application.md)
