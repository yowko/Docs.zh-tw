---
title: HOW TO：使用應用程式範圍的資源字典
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dictionaries [WPF], resource
- resource dictionaries [WPF], application-scope
- application-scope resource dictionaries
ms.assetid: 53857682-bd2c-4f2c-8f25-1307d0b451a2
ms.openlocfilehash: 589e28b3c05496e3fc17055b98240e389faed068
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59125370"
---
# <a name="how-to-use-an-application-scope-resource-dictionary"></a><span data-ttu-id="d1c2c-102">HOW TO：使用應用程式範圍的資源字典</span><span class="sxs-lookup"><span data-stu-id="d1c2c-102">How to: Use an Application-Scope Resource Dictionary</span></span>
<span data-ttu-id="d1c2c-103">此範例示範如何定義和使用應用程式範圍自訂資源字典。</span><span class="sxs-lookup"><span data-stu-id="d1c2c-103">This example shows how to define and use an application-scope custom resource dictionary.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1c2c-104">範例</span><span class="sxs-lookup"><span data-stu-id="d1c2c-104">Example</span></span>  
 <xref:System.Windows.Application> <span data-ttu-id="d1c2c-105">公開共用資源的應用程式範圍存放區： <xref:System.Windows.Application.Resources%2A>。</span><span class="sxs-lookup"><span data-stu-id="d1c2c-105">exposes an application-scope store for shared resources: <xref:System.Windows.Application.Resources%2A>.</span></span> <span data-ttu-id="d1c2c-106">根據預設，<xref:System.Windows.Application.Resources%2A>屬性會初始化的執行個體<xref:System.Windows.ResourceDictionary>型別。</span><span class="sxs-lookup"><span data-stu-id="d1c2c-106">By default, the <xref:System.Windows.Application.Resources%2A> property is initialized with an instance of the <xref:System.Windows.ResourceDictionary> type.</span></span> <span data-ttu-id="d1c2c-107">當您取得和設定應用程式範圍的屬性使用時，會使用此執行個體<xref:System.Windows.Application.Resources%2A>。</span><span class="sxs-lookup"><span data-stu-id="d1c2c-107">You use this instance when you get and set application-scope properties using <xref:System.Windows.Application.Resources%2A>.</span></span> <span data-ttu-id="d1c2c-108">如需詳細資訊，請參閱[如何：取得及設定應用程式範圍資源](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa348547(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="d1c2c-108">For more information, see [How to: Get and Set an Application-Scope Resource](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa348547(v=vs.100)).</span></span>
  
 <span data-ttu-id="d1c2c-109">如果您有多個您設定使用的資源<xref:System.Windows.Application.Resources%2A>，您可以改用自訂資源字典來儲存這些資源和設定<xref:System.Windows.Application.Resources%2A>與其改。</span><span class="sxs-lookup"><span data-stu-id="d1c2c-109">If you have multiple resources that you set using <xref:System.Windows.Application.Resources%2A>, you can instead use a custom resource dictionary to store those resources and set <xref:System.Windows.Application.Resources%2A> with it instead.</span></span> <span data-ttu-id="d1c2c-110">下圖顯示您將自訂資源字典，使用 XAML 的宣告。</span><span class="sxs-lookup"><span data-stu-id="d1c2c-110">The following shows how you declare a custom resource dictionary using XAML.</span></span>
  
 [!code-xaml[HOWTOResourceDictionaries#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MyResourceDictionary.xaml#1)]  
  
 <span data-ttu-id="d1c2c-111">交換整個資源字典使用<xref:System.Windows.Application.Resources%2A>可讓您支援應用程式範圍的主題，其中每個佈景主題所封裝的單一資源字典。</span><span class="sxs-lookup"><span data-stu-id="d1c2c-111">Swapping entire resource dictionaries using <xref:System.Windows.Application.Resources%2A> allows you to support application-scope themes, where each theme is encapsulated by a single resource dictionary.</span></span> <span data-ttu-id="d1c2c-112">下列範例會示範如何設定 <xref:System.Windows.ResourceDictionary>。</span><span class="sxs-lookup"><span data-stu-id="d1c2c-112">The following example shows how to set the <xref:System.Windows.ResourceDictionary>.</span></span>  
  
 [!code-xaml[HOWTOResourceDictionaries#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/App.xaml#2)]  
  
 <span data-ttu-id="d1c2c-113">下列範例示範如何取得應用程式範圍的資源，以及在從所公開的資源字典<xref:System.Windows.Application.Resources%2A>在 XAML 中。</span><span class="sxs-lookup"><span data-stu-id="d1c2c-113">The following shows how you can get application-scope resources from the resource dictionary exposed by <xref:System.Windows.Application.Resources%2A> in XAML.</span></span>  
  
 [!code-xaml[HOWTOResourceDictionaries#4](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml#4)]  
  
 <span data-ttu-id="d1c2c-114">下列會顯示也可以如何使用程式碼來取得資源。</span><span class="sxs-lookup"><span data-stu-id="d1c2c-114">The following shows how you can also get the resources in code.</span></span>  
  
 [!code-csharp[HOWTOResourceDictionaries#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml.cs#3)]
 [!code-vb[HOWTOResourceDictionaries#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToResourceDictionaries/VB/MainWindow.xaml.vb#3)]  
  
 <span data-ttu-id="d1c2c-115">有兩個使用時的考量<xref:System.Windows.Application.Resources%2A>。</span><span class="sxs-lookup"><span data-stu-id="d1c2c-115">There are two considerations to make when using <xref:System.Windows.Application.Resources%2A>.</span></span> <span data-ttu-id="d1c2c-116">首先，字典*金鑰*是一個物件，因此您必須使用完全相同物件執行個體時設定和取得屬性值。</span><span class="sxs-lookup"><span data-stu-id="d1c2c-116">First, the dictionary *key* is an object, so you must use exactly the same object instance when both setting and getting a property value.</span></span> <span data-ttu-id="d1c2c-117">(請注意，使用字串時，索引鍵會區分大小寫)。其次，字典*值*是一個物件，因此您必須將值轉換成所需的型別，取得屬性值時。</span><span class="sxs-lookup"><span data-stu-id="d1c2c-117">(Note that the key is case-sensitive when using a string.) Second, the dictionary *value* is an object, so you will have to convert the value to the desired type when getting a property value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1c2c-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1c2c-118">See also</span></span>

- <xref:System.Windows.ResourceDictionary>
- <xref:System.Windows.Application.Resources%2A>
- [<span data-ttu-id="d1c2c-119">XAML 資源</span><span class="sxs-lookup"><span data-stu-id="d1c2c-119">XAML Resources</span></span>](../advanced/xaml-resources.md)
- [<span data-ttu-id="d1c2c-120">合併的資源字典</span><span class="sxs-lookup"><span data-stu-id="d1c2c-120">Merged Resource Dictionaries</span></span>](../advanced/merged-resource-dictionaries.md)
