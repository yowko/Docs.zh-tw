---
title: 類型 '<typename>' 未定義
ms.date: 07/20/2015
f1_keywords:
- vbc30002
- bc30002
helpviewer_keywords:
- BC30002
ms.assetid: b0faf204-57fd-44de-8c05-9db027eea663
ms.openlocfilehash: 3c22e6a5199bd52cb9fae66a15a66ac9ce095e81
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90872193"
---
# <a name="type-typename-is-not-defined"></a><span data-ttu-id="56cca-102">類型 '\<typename>' 未定義</span><span class="sxs-lookup"><span data-stu-id="56cca-102">Type '\<typename>' is not defined</span></span>

<span data-ttu-id="56cca-103">語句已參考尚未定義的類型。</span><span class="sxs-lookup"><span data-stu-id="56cca-103">The statement has made reference to a type that has not been defined.</span></span> <span data-ttu-id="56cca-104">您可以在宣告語句中定義型別，例如 `Enum` 、 `Structure` 、 `Class` 或 `Interface` 。</span><span class="sxs-lookup"><span data-stu-id="56cca-104">You can define a type in a declaration statement such as `Enum`, `Structure`, `Class`, or `Interface`.</span></span>  
  
 <span data-ttu-id="56cca-105">**錯誤識別碼：** BC30002</span><span class="sxs-lookup"><span data-stu-id="56cca-105">**Error ID:** BC30002</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="56cca-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="56cca-106">To correct this error</span></span>  
  
- <span data-ttu-id="56cca-107">確定類型定義及其參考都使用相同的拼寫。</span><span class="sxs-lookup"><span data-stu-id="56cca-107">Ensure that the type definition and its reference both use the same spelling.</span></span>  
  
- <span data-ttu-id="56cca-108">確定參考可存取型別定義。</span><span class="sxs-lookup"><span data-stu-id="56cca-108">Ensure that the type definition is accessible to the reference.</span></span> <span data-ttu-id="56cca-109">例如，如果類型是在另一個模組中且已宣告 `Private` ，請將類型定義移至參考模組或將其宣告 `Public` 。</span><span class="sxs-lookup"><span data-stu-id="56cca-109">For example, if the type is in another module and has been declared `Private`, move the type definition to the referencing module or declare it `Public`.</span></span>  
  
- <span data-ttu-id="56cca-110">確定您的專案中未重新定義類型的命名空間。</span><span class="sxs-lookup"><span data-stu-id="56cca-110">Ensure that the namespace of the type is not redefined within your project.</span></span> <span data-ttu-id="56cca-111">如果是，請使用 `Global` 關鍵字來完整限定型別名稱。</span><span class="sxs-lookup"><span data-stu-id="56cca-111">If it is, use the `Global` keyword to fully qualify the type name.</span></span> <span data-ttu-id="56cca-112">例如，如果專案定義名為的命名空間 `System` ，則 <xref:System.Object?displayProperty=nameWithType> 無法存取型別，除非它是完整的 `Global` 關鍵字： `Global.System.Object` 。</span><span class="sxs-lookup"><span data-stu-id="56cca-112">For example, if a project defines a namespace named `System`, the <xref:System.Object?displayProperty=nameWithType> type cannot be accessed unless it is fully qualified with the `Global` keyword: `Global.System.Object`.</span></span>  
  
- <span data-ttu-id="56cca-113">如果已定義類型，但未在 Visual Basic 中註冊其定義所在的物件程式庫或類型程式庫，請按一下 [**專案**] 功能表上的 [**加入參考**]，然後選取適當的物件程式庫或型別程式庫。</span><span class="sxs-lookup"><span data-stu-id="56cca-113">If the type is defined, but the object library or type library in which it is defined is not registered in Visual Basic, click **Add Reference** on the **Project** menu, and then select the appropriate object library or type library.</span></span>  
  
- <span data-ttu-id="56cca-114">確定類型是在屬於目標 .NET Framework 設定檔一部分的元件中。</span><span class="sxs-lookup"><span data-stu-id="56cca-114">Ensure that the type is in an assembly that is part of the targeted .NET Framework profile.</span></span> <span data-ttu-id="56cca-115">如需詳細資訊，請參閱[針對 .NET Framework 目標錯誤進行疑難排解](/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors)。</span><span class="sxs-lookup"><span data-stu-id="56cca-115">For more information, see [Troubleshooting .NET Framework Targeting Errors](/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56cca-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="56cca-116">See also</span></span>

- [<span data-ttu-id="56cca-117">Visual Basic 中的命名空間</span><span class="sxs-lookup"><span data-stu-id="56cca-117">Namespaces in Visual Basic</span></span>](../../programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="56cca-118">End 陳述式</span><span class="sxs-lookup"><span data-stu-id="56cca-118">Enum Statement</span></span>](../statements/enum-statement.md)
- [<span data-ttu-id="56cca-119">Structure 陳述式</span><span class="sxs-lookup"><span data-stu-id="56cca-119">Structure Statement</span></span>](../statements/structure-statement.md)
- [<span data-ttu-id="56cca-120">Class 陳述式</span><span class="sxs-lookup"><span data-stu-id="56cca-120">Class Statement</span></span>](../statements/class-statement.md)
- [<span data-ttu-id="56cca-121">Interface 陳述式</span><span class="sxs-lookup"><span data-stu-id="56cca-121">Interface Statement</span></span>](../statements/interface-statement.md)
- [<span data-ttu-id="56cca-122">管理專案中的參考</span><span class="sxs-lookup"><span data-stu-id="56cca-122">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
