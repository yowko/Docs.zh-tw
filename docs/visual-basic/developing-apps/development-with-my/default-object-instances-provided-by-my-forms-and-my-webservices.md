---
title: My.Forms 及 My.WebServices 提供的預設物件執行個體
ms.date: 07/20/2015
helpviewer_keywords:
- My.WebServices object [Visual Basic], developing applications
- My.Forms object [Visual Basic], developing applications
- rapid application development (RAD), My.Forms
- rapid application development (RAD), My.WebServices
ms.assetid: de930027-9108-4f0c-b97c-5e7db4d6ef79
ms.openlocfilehash: 141f2f5f98499498d3c6732f7ae8d0abe6259ed9
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990246"
---
# <a name="default-object-instances-provided-by-myforms-and-mywebservices-visual-basic"></a><span data-ttu-id="9bdd3-102">My.Forms 和 My.WebServices 提供的預設物件執行個體 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9bdd3-102">Default Object Instances Provided by My.Forms and My.WebServices (Visual Basic)</span></span>

<span data-ttu-id="9bdd3-103">[WebServices](../../language-reference/objects/my-webservices-object.md)物件可讓您存取應用程式所[使用的窗](../../language-reference/objects/my-forms-object.md)體、資料來源和 XML Web Service。</span><span class="sxs-lookup"><span data-stu-id="9bdd3-103">The [My.Forms](../../language-reference/objects/my-forms-object.md) and [My.WebServices](../../language-reference/objects/my-webservices-object.md) objects provide access to forms, data sources, and XML Web services used by your application.</span></span> <span data-ttu-id="9bdd3-104">它們會透過每個物件的*預設實例*集合來提供存取權。</span><span class="sxs-lookup"><span data-stu-id="9bdd3-104">They provide access through collections of *default instances* of each of these objects.</span></span>  
  
## <a name="default-instances"></a><span data-ttu-id="9bdd3-105">預設實例</span><span class="sxs-lookup"><span data-stu-id="9bdd3-105">Default Instances</span></span>  

 <span data-ttu-id="9bdd3-106">預設實例是執行時間所提供之類別的實例，不需要使用和語句來宣告和具現化 `Dim` `New` 。</span><span class="sxs-lookup"><span data-stu-id="9bdd3-106">A default instance is an instance of the class that is provided by the runtime and does not need to be declared and instantiated using the `Dim` and `New` statements.</span></span> <span data-ttu-id="9bdd3-107">下列範例示範您可能已經宣告並具現化類別的實例 <xref:System.Windows.Forms.Form> ，而 `Form1` 您現在可以透過取得這個類別的預設實例 <xref:System.Windows.Forms.Form> `My.Forms` 。</span><span class="sxs-lookup"><span data-stu-id="9bdd3-107">The following example demonstrates how you might have declared and instantiated an instance of a <xref:System.Windows.Forms.Form> class called `Form1`, and how you are now able to get a default instance of this <xref:System.Windows.Forms.Form> class through `My.Forms`.</span></span>  
  
 [!code-vb[VbVbcnMy#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#5)]  
  
 [!code-vb[VbVbcnMy#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#6)]  
  
 <span data-ttu-id="9bdd3-108">`My.Forms`物件會針對存在於專案中的每個類別，傳回預設實例的集合 `Form` 。</span><span class="sxs-lookup"><span data-stu-id="9bdd3-108">The `My.Forms` object returns a collection of default instances for every `Form` class that exists in your project.</span></span> <span data-ttu-id="9bdd3-109">同樣地， `My.WebServices` 為您在應用程式中建立參考的每個 Web 服務，提供 proxy 類別的預設實例。</span><span class="sxs-lookup"><span data-stu-id="9bdd3-109">Similarly, `My.WebServices` provides a default instance of the proxy class for every Web service that you have created a reference to in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bdd3-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9bdd3-110">See also</span></span>

- [<span data-ttu-id="9bdd3-111">My.Forms 物件</span><span class="sxs-lookup"><span data-stu-id="9bdd3-111">My.Forms Object</span></span>](../../language-reference/objects/my-forms-object.md)
- [<span data-ttu-id="9bdd3-112">My.WebServices 物件</span><span class="sxs-lookup"><span data-stu-id="9bdd3-112">My.WebServices Object</span></span>](../../language-reference/objects/my-webservices-object.md)
- [<span data-ttu-id="9bdd3-113">My 與專案類型的相依關係</span><span class="sxs-lookup"><span data-stu-id="9bdd3-113">How My Depends on Project Type</span></span>](how-my-depends-on-project-type.md)
