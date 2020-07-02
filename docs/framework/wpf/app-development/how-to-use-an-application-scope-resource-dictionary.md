---
title: 如何：使用應用程式範圍的資源字典
description: 瞭解如何在 Windows Presentation Foundation （WPF）中定義和使用應用程式範圍的自訂資源字典。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dictionaries [WPF], resource
- resource dictionaries [WPF], application-scope
- application-scope resource dictionaries
ms.assetid: 53857682-bd2c-4f2c-8f25-1307d0b451a2
ms.openlocfilehash: 9d117dea6c554339b4b462b9bf37b80da2dc477f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85613705"
---
# <a name="how-to-use-an-application-scope-resource-dictionary"></a><span data-ttu-id="66f7a-103">如何：使用應用程式範圍的資源字典</span><span class="sxs-lookup"><span data-stu-id="66f7a-103">How to: Use an Application-Scope Resource Dictionary</span></span>
<span data-ttu-id="66f7a-104">此範例示範如何定義和使用應用程式範圍自訂資源字典。</span><span class="sxs-lookup"><span data-stu-id="66f7a-104">This example shows how to define and use an application-scope custom resource dictionary.</span></span>  
  
## <a name="example"></a><span data-ttu-id="66f7a-105">範例</span><span class="sxs-lookup"><span data-stu-id="66f7a-105">Example</span></span>  
 <span data-ttu-id="66f7a-106"><xref:System.Windows.Application>公開共用資源的應用程式範圍存放區： <xref:System.Windows.Application.Resources%2A> 。</span><span class="sxs-lookup"><span data-stu-id="66f7a-106"><xref:System.Windows.Application> exposes an application-scope store for shared resources: <xref:System.Windows.Application.Resources%2A>.</span></span> <span data-ttu-id="66f7a-107">根據預設， <xref:System.Windows.Application.Resources%2A> 會使用類型的實例來初始化屬性 <xref:System.Windows.ResourceDictionary> 。</span><span class="sxs-lookup"><span data-stu-id="66f7a-107">By default, the <xref:System.Windows.Application.Resources%2A> property is initialized with an instance of the <xref:System.Windows.ResourceDictionary> type.</span></span> <span data-ttu-id="66f7a-108">當您使用來取得和設定應用程式範圍的屬性時，會使用這個實例 <xref:System.Windows.Application.Resources%2A> 。</span><span class="sxs-lookup"><span data-stu-id="66f7a-108">You use this instance when you get and set application-scope properties using <xref:System.Windows.Application.Resources%2A>.</span></span> <span data-ttu-id="66f7a-109">如需詳細資訊，請參閱[如何：取得和設定應用程式範圍的資源](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa348547(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="66f7a-109">For more information, see [How to: Get and Set an Application-Scope Resource](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa348547(v=vs.100)).</span></span>
  
 <span data-ttu-id="66f7a-110">如果您有使用設定的多個資源 <xref:System.Windows.Application.Resources%2A> ，則可以改為使用自訂資源字典來儲存這些資源，並 <xref:System.Windows.Application.Resources%2A> 改為加以設定。</span><span class="sxs-lookup"><span data-stu-id="66f7a-110">If you have multiple resources that you set using <xref:System.Windows.Application.Resources%2A>, you can instead use a custom resource dictionary to store those resources and set <xref:System.Windows.Application.Resources%2A> with it instead.</span></span> <span data-ttu-id="66f7a-111">以下顯示如何使用 XAML 宣告自訂資源字典。</span><span class="sxs-lookup"><span data-stu-id="66f7a-111">The following shows how you declare a custom resource dictionary using XAML.</span></span>
  
 [!code-xaml[HOWTOResourceDictionaries#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MyResourceDictionary.xaml#1)]  
  
 <span data-ttu-id="66f7a-112">使用交換整個資源字典 <xref:System.Windows.Application.Resources%2A> ，可讓您支援應用程式範圍主題，其中每個主題都是由單一資源字典封裝。</span><span class="sxs-lookup"><span data-stu-id="66f7a-112">Swapping entire resource dictionaries using <xref:System.Windows.Application.Resources%2A> allows you to support application-scope themes, where each theme is encapsulated by a single resource dictionary.</span></span> <span data-ttu-id="66f7a-113">下列範例會示範如何設定 <xref:System.Windows.ResourceDictionary>。</span><span class="sxs-lookup"><span data-stu-id="66f7a-113">The following example shows how to set the <xref:System.Windows.ResourceDictionary>.</span></span>  
  
 [!code-xaml[HOWTOResourceDictionaries#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/App.xaml#2)]  
  
 <span data-ttu-id="66f7a-114">以下顯示如何從 XAML 中所公開的資源字典取得應用程式範圍的資源 <xref:System.Windows.Application.Resources%2A> 。</span><span class="sxs-lookup"><span data-stu-id="66f7a-114">The following shows how you can get application-scope resources from the resource dictionary exposed by <xref:System.Windows.Application.Resources%2A> in XAML.</span></span>  
  
 [!code-xaml[HOWTOResourceDictionaries#4](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml#4)]  
  
 <span data-ttu-id="66f7a-115">下列會顯示也可以如何使用程式碼來取得資源。</span><span class="sxs-lookup"><span data-stu-id="66f7a-115">The following shows how you can also get the resources in code.</span></span>  
  
 [!code-csharp[HOWTOResourceDictionaries#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml.cs#3)]
 [!code-vb[HOWTOResourceDictionaries#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToResourceDictionaries/VB/MainWindow.xaml.vb#3)]  
  
 <span data-ttu-id="66f7a-116">使用時，有兩個要進行的考慮 <xref:System.Windows.Application.Resources%2A> 。</span><span class="sxs-lookup"><span data-stu-id="66f7a-116">There are two considerations to make when using <xref:System.Windows.Application.Resources%2A>.</span></span> <span data-ttu-id="66f7a-117">首先，字典索引*鍵*是物件，因此當您設定並取得屬性值時，必須使用完全相同的物件實例。</span><span class="sxs-lookup"><span data-stu-id="66f7a-117">First, the dictionary *key* is an object, so you must use exactly the same object instance when both setting and getting a property value.</span></span> <span data-ttu-id="66f7a-118">（請注意，使用字串時，索引鍵會區分大小寫）。第二，字典*值*是物件，因此，您必須在取得屬性值時，將值轉換成所需的類型。</span><span class="sxs-lookup"><span data-stu-id="66f7a-118">(Note that the key is case-sensitive when using a string.) Second, the dictionary *value* is an object, so you will have to convert the value to the desired type when getting a property value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66f7a-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="66f7a-119">See also</span></span>

- <xref:System.Windows.ResourceDictionary>
- <xref:System.Windows.Application.Resources%2A>
- [<span data-ttu-id="66f7a-120">XAML 資源</span><span class="sxs-lookup"><span data-stu-id="66f7a-120">XAML Resources</span></span>](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [<span data-ttu-id="66f7a-121">合併的資源字典</span><span class="sxs-lookup"><span data-stu-id="66f7a-121">Merged Resource Dictionaries</span></span>](../advanced/merged-resource-dictionaries.md)
