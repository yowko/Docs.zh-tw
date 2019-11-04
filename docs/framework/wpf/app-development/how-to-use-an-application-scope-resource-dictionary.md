---
title: 如何：使用應用程式範圍的資源字典
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dictionaries [WPF], resource
- resource dictionaries [WPF], application-scope
- application-scope resource dictionaries
ms.assetid: 53857682-bd2c-4f2c-8f25-1307d0b451a2
ms.openlocfilehash: 5bfb3ed0304598a5acf4b7682bf4a4169c5153d1
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459792"
---
# <a name="how-to-use-an-application-scope-resource-dictionary"></a><span data-ttu-id="43277-102">如何：使用應用程式範圍的資源字典</span><span class="sxs-lookup"><span data-stu-id="43277-102">How to: Use an Application-Scope Resource Dictionary</span></span>
<span data-ttu-id="43277-103">此範例示範如何定義和使用應用程式範圍自訂資源字典。</span><span class="sxs-lookup"><span data-stu-id="43277-103">This example shows how to define and use an application-scope custom resource dictionary.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43277-104">範例</span><span class="sxs-lookup"><span data-stu-id="43277-104">Example</span></span>  
 <span data-ttu-id="43277-105"><xref:System.Windows.Application> 會公開共用資源的應用程式範圍存放區： <xref:System.Windows.Application.Resources%2A>。</span><span class="sxs-lookup"><span data-stu-id="43277-105"><xref:System.Windows.Application> exposes an application-scope store for shared resources: <xref:System.Windows.Application.Resources%2A>.</span></span> <span data-ttu-id="43277-106">根據預設，<xref:System.Windows.Application.Resources%2A> 屬性會使用 <xref:System.Windows.ResourceDictionary> 類型的實例進行初始化。</span><span class="sxs-lookup"><span data-stu-id="43277-106">By default, the <xref:System.Windows.Application.Resources%2A> property is initialized with an instance of the <xref:System.Windows.ResourceDictionary> type.</span></span> <span data-ttu-id="43277-107">當您使用 <xref:System.Windows.Application.Resources%2A>取得和設定應用程式範圍的屬性時，會使用這個實例。</span><span class="sxs-lookup"><span data-stu-id="43277-107">You use this instance when you get and set application-scope properties using <xref:System.Windows.Application.Resources%2A>.</span></span> <span data-ttu-id="43277-108">如需詳細資訊，請參閱[如何：取得和設定應用程式範圍的資源](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa348547(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="43277-108">For more information, see [How to: Get and Set an Application-Scope Resource](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa348547(v=vs.100)).</span></span>
  
 <span data-ttu-id="43277-109">如果您有多個使用 <xref:System.Windows.Application.Resources%2A>設定的資源，您可以改為使用自訂資源字典來儲存這些資源，並改為設定 <xref:System.Windows.Application.Resources%2A>。</span><span class="sxs-lookup"><span data-stu-id="43277-109">If you have multiple resources that you set using <xref:System.Windows.Application.Resources%2A>, you can instead use a custom resource dictionary to store those resources and set <xref:System.Windows.Application.Resources%2A> with it instead.</span></span> <span data-ttu-id="43277-110">以下顯示如何使用 XAML 宣告自訂資源字典。</span><span class="sxs-lookup"><span data-stu-id="43277-110">The following shows how you declare a custom resource dictionary using XAML.</span></span>
  
 [!code-xaml[HOWTOResourceDictionaries#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MyResourceDictionary.xaml#1)]  
  
 <span data-ttu-id="43277-111">使用 <xref:System.Windows.Application.Resources%2A> 交換整個資源字典可讓您支援應用程式範圍主題，其中每個主題都是由單一資源字典封裝。</span><span class="sxs-lookup"><span data-stu-id="43277-111">Swapping entire resource dictionaries using <xref:System.Windows.Application.Resources%2A> allows you to support application-scope themes, where each theme is encapsulated by a single resource dictionary.</span></span> <span data-ttu-id="43277-112">下列範例會示範如何設定 <xref:System.Windows.ResourceDictionary>。</span><span class="sxs-lookup"><span data-stu-id="43277-112">The following example shows how to set the <xref:System.Windows.ResourceDictionary>.</span></span>  
  
 [!code-xaml[HOWTOResourceDictionaries#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/App.xaml#2)]  
  
 <span data-ttu-id="43277-113">以下顯示如何從 XAML 中 <xref:System.Windows.Application.Resources%2A> 所公開的資源字典取得應用程式範圍的資源。</span><span class="sxs-lookup"><span data-stu-id="43277-113">The following shows how you can get application-scope resources from the resource dictionary exposed by <xref:System.Windows.Application.Resources%2A> in XAML.</span></span>  
  
 [!code-xaml[HOWTOResourceDictionaries#4](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml#4)]  
  
 <span data-ttu-id="43277-114">下列會顯示也可以如何使用程式碼來取得資源。</span><span class="sxs-lookup"><span data-stu-id="43277-114">The following shows how you can also get the resources in code.</span></span>  
  
 [!code-csharp[HOWTOResourceDictionaries#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml.cs#3)]
 [!code-vb[HOWTOResourceDictionaries#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToResourceDictionaries/VB/MainWindow.xaml.vb#3)]  
  
 <span data-ttu-id="43277-115">使用 <xref:System.Windows.Application.Resources%2A>時，需要進行兩個考慮。</span><span class="sxs-lookup"><span data-stu-id="43277-115">There are two considerations to make when using <xref:System.Windows.Application.Resources%2A>.</span></span> <span data-ttu-id="43277-116">首先，字典索引*鍵*是物件，因此當您設定並取得屬性值時，必須使用完全相同的物件實例。</span><span class="sxs-lookup"><span data-stu-id="43277-116">First, the dictionary *key* is an object, so you must use exactly the same object instance when both setting and getting a property value.</span></span> <span data-ttu-id="43277-117">（請注意，使用字串時，索引鍵會區分大小寫）。第二，字典*值*是物件，因此，您必須在取得屬性值時，將值轉換成所需的類型。</span><span class="sxs-lookup"><span data-stu-id="43277-117">(Note that the key is case-sensitive when using a string.) Second, the dictionary *value* is an object, so you will have to convert the value to the desired type when getting a property value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43277-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="43277-118">See also</span></span>

- <xref:System.Windows.ResourceDictionary>
- <xref:System.Windows.Application.Resources%2A>
- [<span data-ttu-id="43277-119">XAML 資源</span><span class="sxs-lookup"><span data-stu-id="43277-119">XAML Resources</span></span>](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [<span data-ttu-id="43277-120">合併的資源字典</span><span class="sxs-lookup"><span data-stu-id="43277-120">Merged Resource Dictionaries</span></span>](../advanced/merged-resource-dictionaries.md)
