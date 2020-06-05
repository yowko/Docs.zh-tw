---
title: 類型 '<typename>' 未定義
ms.date: 07/20/2015
f1_keywords:
- vbc30002
- bc30002
helpviewer_keywords:
- BC30002
ms.assetid: b0faf204-57fd-44de-8c05-9db027eea663
ms.openlocfilehash: 89e2d1d18b456c96f62d6b9ee1dd8dc9d41bf665
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84386928"
---
# <a name="type-typename-is-not-defined"></a><span data-ttu-id="a676f-102">類型 '\<typename>' 未定義</span><span class="sxs-lookup"><span data-stu-id="a676f-102">Type '\<typename>' is not defined</span></span>
<span data-ttu-id="a676f-103">語句已參考尚未定義的類型。</span><span class="sxs-lookup"><span data-stu-id="a676f-103">The statement has made reference to a type that has not been defined.</span></span> <span data-ttu-id="a676f-104">您可以在宣告語句中定義類型 `Enum` ，例如、 `Structure` 、 `Class` 或 `Interface` 。</span><span class="sxs-lookup"><span data-stu-id="a676f-104">You can define a type in a declaration statement such as `Enum`, `Structure`, `Class`, or `Interface`.</span></span>  
  
 <span data-ttu-id="a676f-105">**錯誤識別碼：** BC30002</span><span class="sxs-lookup"><span data-stu-id="a676f-105">**Error ID:** BC30002</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a676f-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="a676f-106">To correct this error</span></span>  
  
- <span data-ttu-id="a676f-107">請確定類型定義及其參考皆使用相同的拼寫。</span><span class="sxs-lookup"><span data-stu-id="a676f-107">Ensure that the type definition and its reference both use the same spelling.</span></span>  
  
- <span data-ttu-id="a676f-108">請確定類型定義可供參考存取。</span><span class="sxs-lookup"><span data-stu-id="a676f-108">Ensure that the type definition is accessible to the reference.</span></span> <span data-ttu-id="a676f-109">例如，如果類型是在另一個模組中且已宣告 `Private` ，請將類型定義移至參考模組，或將其宣告 `Public` 。</span><span class="sxs-lookup"><span data-stu-id="a676f-109">For example, if the type is in another module and has been declared `Private`, move the type definition to the referencing module or declare it `Public`.</span></span>  
  
- <span data-ttu-id="a676f-110">請確定您的專案中未重新定義類型的命名空間。</span><span class="sxs-lookup"><span data-stu-id="a676f-110">Ensure that the namespace of the type is not redefined within your project.</span></span> <span data-ttu-id="a676f-111">如果是，請使用 `Global` 關鍵字來完整限定型別名稱。</span><span class="sxs-lookup"><span data-stu-id="a676f-111">If it is, use the `Global` keyword to fully qualify the type name.</span></span> <span data-ttu-id="a676f-112">例如，如果專案定義名為的命名空間 `System` ，則 <xref:System.Object?displayProperty=nameWithType> 無法存取類型，除非它是以關鍵字完整限定的 `Global` ： `Global.System.Object` 。</span><span class="sxs-lookup"><span data-stu-id="a676f-112">For example, if a project defines a namespace named `System`, the <xref:System.Object?displayProperty=nameWithType> type cannot be accessed unless it is fully qualified with the `Global` keyword: `Global.System.Object`.</span></span>  
  
- <span data-ttu-id="a676f-113">如果已定義類型，但未在 Visual Basic 中註冊其定義所在的物件程式庫或類型程式庫，請按一下 [**專案**] 功能表上的 [**加入參考**]，然後選取適當的物件程式庫或類型程式庫。</span><span class="sxs-lookup"><span data-stu-id="a676f-113">If the type is defined, but the object library or type library in which it is defined is not registered in Visual Basic, click **Add Reference** on the **Project** menu, and then select the appropriate object library or type library.</span></span>  
  
- <span data-ttu-id="a676f-114">請確定該類型位於屬於目標 .NET Framework 設定檔一部分的元件中。</span><span class="sxs-lookup"><span data-stu-id="a676f-114">Ensure that the type is in an assembly that is part of the targeted .NET Framework profile.</span></span> <span data-ttu-id="a676f-115">如需詳細資訊，請參閱[針對 .NET Framework 目標錯誤進行疑難排解](/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors)。</span><span class="sxs-lookup"><span data-stu-id="a676f-115">For more information, see [Troubleshooting .NET Framework Targeting Errors](/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a676f-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a676f-116">See also</span></span>

- [<span data-ttu-id="a676f-117">Visual Basic 中的命名空間</span><span class="sxs-lookup"><span data-stu-id="a676f-117">Namespaces in Visual Basic</span></span>](../../programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="a676f-118">End 陳述式</span><span class="sxs-lookup"><span data-stu-id="a676f-118">Enum Statement</span></span>](../statements/enum-statement.md)
- [<span data-ttu-id="a676f-119">Structure 陳述式</span><span class="sxs-lookup"><span data-stu-id="a676f-119">Structure Statement</span></span>](../statements/structure-statement.md)
- [<span data-ttu-id="a676f-120">Class 陳述式</span><span class="sxs-lookup"><span data-stu-id="a676f-120">Class Statement</span></span>](../statements/class-statement.md)
- [<span data-ttu-id="a676f-121">Interface 陳述式</span><span class="sxs-lookup"><span data-stu-id="a676f-121">Interface Statement</span></span>](../statements/interface-statement.md)
- [<span data-ttu-id="a676f-122">管理專案中的參考</span><span class="sxs-lookup"><span data-stu-id="a676f-122">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
