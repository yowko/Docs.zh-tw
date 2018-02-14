---
title: "如何：防止子工作附加到其父代"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, preventing attachments
ms.assetid: c0fb85d4-9e80-4905-9f65-29acc54201c4
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2cab2fb9c26a8ddaa868cafebac718e5dfd6baa0
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-prevent-a-child-task-from-attaching-to-its-parent"></a><span data-ttu-id="982e2-102">如何：防止子工作附加到其父代</span><span class="sxs-lookup"><span data-stu-id="982e2-102">How to: Prevent a Child Task from Attaching to its Parent</span></span>
<span data-ttu-id="982e2-103">本文件將示範如何防止將子工作附加至父工作。</span><span class="sxs-lookup"><span data-stu-id="982e2-103">This document demonstrates how to prevent a child task from attaching to the parent task.</span></span> <span data-ttu-id="982e2-104">如果您呼叫的元件是由協力廠商所撰寫，而且也會使用工作，則防止子工作附加至其父代會很實用。</span><span class="sxs-lookup"><span data-stu-id="982e2-104">Preventing a child task from attaching to its parent is useful when you call a component that is written by a third party and that also uses tasks.</span></span> <span data-ttu-id="982e2-105">例如，如果使用 <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> 選項建立 <xref:System.Threading.Tasks.Task> 或 <xref:System.Threading.Tasks.Task%601> 物件的協力廠商元件會長時間執行或擲回未處理的例外狀況，則可能造成程式碼發生問題。</span><span class="sxs-lookup"><span data-stu-id="982e2-105">For example, a third-party component that uses the <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> option to create a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> object can cause problems in your code if it is long-running or throws an unhandled exception.</span></span>  
  
## <a name="example"></a><span data-ttu-id="982e2-106">範例</span><span class="sxs-lookup"><span data-stu-id="982e2-106">Example</span></span>  
 <span data-ttu-id="982e2-107">下列範例會比較使用預設選項的效果，以及防止子工作附加至父工作的效果。</span><span class="sxs-lookup"><span data-stu-id="982e2-107">The following example compares the effects of using the default options to the effects of preventing a child task from attaching to the parent.</span></span> <span data-ttu-id="982e2-108">這個範例會建立 <xref:System.Threading.Tasks.Task> 物件，該物件會呼叫同樣使用 <xref:System.Threading.Tasks.Task> 物件的協力廠商程式庫。</span><span class="sxs-lookup"><span data-stu-id="982e2-108">The example creates a <xref:System.Threading.Tasks.Task> object that calls into a third-party library that also uses a <xref:System.Threading.Tasks.Task> object.</span></span> <span data-ttu-id="982e2-109">協力廠商程式庫會使用 <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> 選項建立 <xref:System.Threading.Tasks.Task> 物件。</span><span class="sxs-lookup"><span data-stu-id="982e2-109">The third-party library uses the <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> option to create the <xref:System.Threading.Tasks.Task> object.</span></span> <span data-ttu-id="982e2-110">應用程式會使用 <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> 選項建立父工作。</span><span class="sxs-lookup"><span data-stu-id="982e2-110">The application uses the <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> option to create the parent task.</span></span> <span data-ttu-id="982e2-111">這個選項會指示執行階段移除子工作中的 <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> 規格。</span><span class="sxs-lookup"><span data-stu-id="982e2-111">This option instructs the runtime to remove the <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> specification in child tasks.</span></span>  
  
 [!code-csharp[TPL_DenyChildAttach#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_denychildattach/cs/denychildattach.cs#1)]
 [!code-vb[TPL_DenyChildAttach#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_denychildattach/vb/denychildattach.vb#1)]  
  
 <span data-ttu-id="982e2-112">由於父工作會在所有子工作完成後才完成，因此長時間執行的子工作可能造成整個應用程式效能不佳。</span><span class="sxs-lookup"><span data-stu-id="982e2-112">Because a parent task does not finish until all child tasks finish, a long-running child task can cause the overall application to perform poorly.</span></span> <span data-ttu-id="982e2-113">在這個範例中，當應用程式使用預設選項建立父工作時，子工作必須在父工作完成之前完成。</span><span class="sxs-lookup"><span data-stu-id="982e2-113">In this example, when the application uses the default options to create the parent task, the child task must finish before the parent task finishes.</span></span> <span data-ttu-id="982e2-114">當應用程式使用 <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> 選項時，子工作不會附加至父工作。</span><span class="sxs-lookup"><span data-stu-id="982e2-114">When the application uses the <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> option, the child is not attached to the parent.</span></span> <span data-ttu-id="982e2-115">因此，應用程式可以在父工作完成之後，以及必須等候子工作完成之前執行其他工作。</span><span class="sxs-lookup"><span data-stu-id="982e2-115">Therefore, the application can perform additional work after the parent task finishes and before it must wait for the child task to finish.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="982e2-116">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="982e2-116">Compiling the Code</span></span>  
 <span data-ttu-id="982e2-117">請複製範例程式碼，並將它貼入 Visual Studio 專案中，或是貼入名為 `DenyChildAttach.cs` 的檔案中 (在 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]中為 `DenyChildAttach.vb`)，然後在 Visual Studio 的 [命令提示字元] 視窗中執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="982e2-117">Copy the example code and paste it in a Visual Studio project, or paste it in a file that is named `DenyChildAttach.cs` (`DenyChildAttach.vb` for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), and then run the following command in a Visual Studio Command Prompt window.</span></span>  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 <span data-ttu-id="982e2-118">**csc.exe DenyChildAttach.cs**</span><span class="sxs-lookup"><span data-stu-id="982e2-118">**csc.exe DenyChildAttach.cs**</span></span>  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 <span data-ttu-id="982e2-119">**vbc.exe DenyChildAttach.vb**</span><span class="sxs-lookup"><span data-stu-id="982e2-119">**vbc.exe DenyChildAttach.vb**</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="982e2-120">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="982e2-120">Robust Programming</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="982e2-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="982e2-121">See Also</span></span>  
 [<span data-ttu-id="982e2-122">以工作為基礎的非同步程式設計</span><span class="sxs-lookup"><span data-stu-id="982e2-122">Task-based Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
