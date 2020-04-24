---
title: My.Forms 及 My.WebServices 提供的預設物件執行個體
ms.date: 07/20/2015
helpviewer_keywords:
- My.WebServices object [Visual Basic], developing applications
- My.Forms object [Visual Basic], developing applications
- rapid application development (RAD), My.Forms
- rapid application development (RAD), My.WebServices
ms.assetid: de930027-9108-4f0c-b97c-5e7db4d6ef79
ms.openlocfilehash: d06df4bd023892429b2aaefdd624398a6546d06d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74330211"
---
# <a name="default-object-instances-provided-by-myforms-and-mywebservices-visual-basic"></a><span data-ttu-id="c5f6f-102">My.Forms 和 My.WebServices 提供的預設物件執行個體 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c5f6f-102">Default Object Instances Provided by My.Forms and My.WebServices (Visual Basic)</span></span>

<span data-ttu-id="c5f6f-103">[WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md)物件可讓您存取應用程式所[使用的窗](../../../visual-basic/language-reference/objects/my-forms-object.md)體、資料來源和 XML Web Service。</span><span class="sxs-lookup"><span data-stu-id="c5f6f-103">The [My.Forms](../../../visual-basic/language-reference/objects/my-forms-object.md) and [My.WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md) objects provide access to forms, data sources, and XML Web services used by your application.</span></span> <span data-ttu-id="c5f6f-104">他們會藉由提供每個物件的*預設實例*集合來執行這項操作。</span><span class="sxs-lookup"><span data-stu-id="c5f6f-104">They do this by providing collections of *default instances* of each of these objects.</span></span>  
  
## <a name="default-instances"></a><span data-ttu-id="c5f6f-105">預設實例</span><span class="sxs-lookup"><span data-stu-id="c5f6f-105">Default Instances</span></span>  

 <span data-ttu-id="c5f6f-106">預設實例是執行時間所提供之類別的實例，不需要使用`Dim`和`New`語句來宣告和具現化。</span><span class="sxs-lookup"><span data-stu-id="c5f6f-106">A default instance is an instance of the class that is provided by the runtime and does not need to be declared and instantiated using the `Dim` and `New` statements.</span></span> <span data-ttu-id="c5f6f-107">下列範例示範您可能已經宣告並<xref:System.Windows.Forms.Form>具現化類別的實例`Form1`，而您現在可以透過<xref:System.Windows.Forms.Form> `My.Forms`取得這個類別的預設實例。</span><span class="sxs-lookup"><span data-stu-id="c5f6f-107">The following example demonstrates how you might have declared and instantiated an instance of a <xref:System.Windows.Forms.Form> class called `Form1`, and how you are now able to get a default instance of this <xref:System.Windows.Forms.Form> class through `My.Forms`.</span></span>  
  
 [!code-vb[VbVbcnMy#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#5)]  
  
 [!code-vb[VbVbcnMy#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#6)]  
  
 <span data-ttu-id="c5f6f-108">`My.Forms`物件會針對存在於專案中的每個`Form`類別，傳回預設實例的集合。</span><span class="sxs-lookup"><span data-stu-id="c5f6f-108">The `My.Forms` object returns a collection of default instances for every `Form` class that exists in your project.</span></span> <span data-ttu-id="c5f6f-109">同樣地`My.WebServices` ，為您在應用程式中建立參考的每個 Web 服務，提供 proxy 類別的預設實例。</span><span class="sxs-lookup"><span data-stu-id="c5f6f-109">Similarly, `My.WebServices` provides a default instance of the proxy class for every Web service that you have created a reference to in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5f6f-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c5f6f-110">See also</span></span>

- [<span data-ttu-id="c5f6f-111">My.Forms 物件</span><span class="sxs-lookup"><span data-stu-id="c5f6f-111">My.Forms Object</span></span>](../../../visual-basic/language-reference/objects/my-forms-object.md)
- [<span data-ttu-id="c5f6f-112">My.WebServices 物件</span><span class="sxs-lookup"><span data-stu-id="c5f6f-112">My.WebServices Object</span></span>](../../../visual-basic/language-reference/objects/my-webservices-object.md)
- [<span data-ttu-id="c5f6f-113">My 如何相依於專案類型</span><span class="sxs-lookup"><span data-stu-id="c5f6f-113">How My Depends on Project Type</span></span>](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
