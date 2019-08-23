---
title: 早期和晚期繫結 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- early binding [Visual Basic]
- objects [Visual Basic], late-bound
- objects [Visual Basic], early-bound
- objects [Visual Basic], late bound
- early binding [Visual Basic], Visual Basic compiler
- binding [Visual Basic], late and early
- objects [Visual Basic], early bound
- Visual Basic compiler, early and late binding
- late binding [Visual Basic]
- late binding [Visual Basic], Visual Basic compiler
ms.assetid: d6ff7f1e-b94f-4205-ab8d-5cfa91758724
ms.openlocfilehash: d05322ba831aac6173ac9d7fa7f369a208b676d0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965383"
---
# <a name="early-and-late-binding-visual-basic"></a><span data-ttu-id="dcb20-102">早期和晚期繫結 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dcb20-102">Early and Late Binding (Visual Basic)</span></span>
<span data-ttu-id="dcb20-103">當物件指派給物件變數時`binding` , Visual Basic 編譯器會執行名為的進程。</span><span class="sxs-lookup"><span data-stu-id="dcb20-103">The Visual Basic compiler performs a process called `binding` when an object is assigned to an object variable.</span></span> <span data-ttu-id="dcb20-104">將物件指派給宣告為特定物件型別的變數時，該物件即為「早期繫結」。</span><span class="sxs-lookup"><span data-stu-id="dcb20-104">An object is *early bound* when it is assigned to a variable declared to be of a specific object type.</span></span> <span data-ttu-id="dcb20-105">早期繫結物件讓編譯器能夠配置記憶體，並在應用程式執行之前執行其他最佳化。</span><span class="sxs-lookup"><span data-stu-id="dcb20-105">Early bound objects allow the compiler to allocate memory and perform other optimizations before an application executes.</span></span> <span data-ttu-id="dcb20-106">例如，下列程式碼片段會將變數宣告為 <xref:System.IO.FileStream> 類型：</span><span class="sxs-lookup"><span data-stu-id="dcb20-106">For example, the following code fragment declares a variable to be of type <xref:System.IO.FileStream>:</span></span>  
  
 [!code-vb[VbVbalrOOP#90](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#90)]  
  
 <span data-ttu-id="dcb20-107">因為 <xref:System.IO.FileStream> 是特定的物件類型，所以指派給 `FS` 的執行個體就是早期繫結。</span><span class="sxs-lookup"><span data-stu-id="dcb20-107">Because <xref:System.IO.FileStream> is a specific object type, the instance assigned to `FS` is early bound.</span></span>  
  
 <span data-ttu-id="dcb20-108">反之，將物件指派給宣告為 `Object` 型別的變數時，該物件即為「晚期繫結」。</span><span class="sxs-lookup"><span data-stu-id="dcb20-108">By contrast, an object is *late bound* when it is assigned to a variable declared to be of type `Object`.</span></span> <span data-ttu-id="dcb20-109">此型別的物件可以保存對任何物件的參考，但缺少許多早期繫結物件的優點。</span><span class="sxs-lookup"><span data-stu-id="dcb20-109">Objects of this type can hold references to any object, but lack many of the advantages of early-bound objects.</span></span> <span data-ttu-id="dcb20-110">例如，下列程式碼片段會宣告一個物件變數來保存 `CreateObject` 函式所傳回的物件：</span><span class="sxs-lookup"><span data-stu-id="dcb20-110">For example, the following code fragment declares an object variable to hold an object returned by the `CreateObject` function:</span></span>  
  
 [!code-vb[VbVbalrOOP#91](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/LateBinding.vb#91)]  
  
## <a name="advantages-of-early-binding"></a><span data-ttu-id="dcb20-111">早期繫結的優點</span><span class="sxs-lookup"><span data-stu-id="dcb20-111">Advantages of Early Binding</span></span>  
 <span data-ttu-id="dcb20-112">您應該盡可能使用早期繫結物件，因為它們可讓編譯器進行重要的最佳化，以產生更有效率的應用程式。</span><span class="sxs-lookup"><span data-stu-id="dcb20-112">You should use early-bound objects whenever possible, because they allow the compiler to make important optimizations that yield more efficient applications.</span></span> <span data-ttu-id="dcb20-113">早期繫結物件的速度很明顯地比晚期繫結物件還快，並藉由確實描述正在使用哪種物件，讓您的程式碼更容易閱讀和維護。</span><span class="sxs-lookup"><span data-stu-id="dcb20-113">Early-bound objects are significantly faster than late-bound objects and make your code easier to read and maintain by stating exactly what kind of objects are being used.</span></span> <span data-ttu-id="dcb20-114">早期繫結的另一個優點是它會啟用有用的功能, 例如自動程式碼完成和動態說明, 因為 Visual Studio 的整合式開發環境 (IDE) 可以在您編輯時, 判斷您要使用的物件類型。錯誤碼.</span><span class="sxs-lookup"><span data-stu-id="dcb20-114">Another advantage to early binding is that it enables useful features such as automatic code completion and Dynamic Help because the Visual Studio integrated development environment (IDE) can determine exactly what type of object you are working with as you edit the code.</span></span> <span data-ttu-id="dcb20-115">早期繫結可降低發生執行階段錯誤的次數和嚴重性，因為它讓編譯器能夠在編譯程式時報告錯誤。</span><span class="sxs-lookup"><span data-stu-id="dcb20-115">Early binding reduces the number and severity of run-time errors because it allows the compiler to report errors when a program is compiled.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dcb20-116">晚期繫結只能用來存取宣告為 `Public` 的型別成員。</span><span class="sxs-lookup"><span data-stu-id="dcb20-116">Late binding can only be used to access type members that are declared as `Public`.</span></span> <span data-ttu-id="dcb20-117">存取宣告為 `Friend` 或 `Protected Friend` 的成員會導致執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="dcb20-117">Accessing members declared as `Friend` or `Protected Friend` results in a run-time error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcb20-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dcb20-118">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.CreateObject%2A>
- [<span data-ttu-id="dcb20-119">物件存留期:物件的建立和終結方式</span><span class="sxs-lookup"><span data-stu-id="dcb20-119">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
- [<span data-ttu-id="dcb20-120">Object 資料類型</span><span class="sxs-lookup"><span data-stu-id="dcb20-120">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
