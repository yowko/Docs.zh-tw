---
title: 讀取和寫入登錄
ms.date: 07/20/2015
helpviewer_keywords:
- My.Computer.Registry object, tasks
- registry [Visual Basic], writing to
- registry [Visual Basic], reading
ms.assetid: a13da106-185b-41d7-b23c-416da65e21e4
ms.openlocfilehash: bb400ef89edaa4eb743aee3a7f2cc5b9dfec4534
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84360055"
---
# <a name="reading-from-and-writing-to-the-registry-visual-basic"></a><span data-ttu-id="2bcea-102">讀取和寫入登錄 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2bcea-102">Reading from and Writing to the Registry (Visual Basic)</span></span>

<span data-ttu-id="2bcea-103">本主題描述與登錄建立關聯的工作和概念主題。</span><span class="sxs-lookup"><span data-stu-id="2bcea-103">This topic describes task and conceptual topics that are associated with the registry.</span></span>  
  
 <span data-ttu-id="2bcea-104">在 Visual Basic 中進行程式設計時，您可以選擇透過 Visual Basic 所提供的函式或是 .NET Framework 的登錄類別來存取登錄。</span><span class="sxs-lookup"><span data-stu-id="2bcea-104">When programming in Visual Basic, you can choose to access the registry by means of either the functions provided by Visual Basic or the registry classes of the .NET Framework.</span></span> <span data-ttu-id="2bcea-105">登錄會裝載作業系統的資訊，以及電腦所裝載的應用程式的資訊。</span><span class="sxs-lookup"><span data-stu-id="2bcea-105">The registry hosts information from the operating system as well as information from applications hosted on the machine.</span></span> <span data-ttu-id="2bcea-106">如果允許不適當地存取系統資源或受保護資訊，則使用登錄可能會危及安全性。</span><span class="sxs-lookup"><span data-stu-id="2bcea-106">Working with the registry may compromise security by allowing inappropriate access to system resources or protected information.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2bcea-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="2bcea-107">In This Section</span></span>  

 [<span data-ttu-id="2bcea-108">作法：建立登錄機碼並設定其值</span><span class="sxs-lookup"><span data-stu-id="2bcea-108">How to: Create a Registry Key and Set Its Value</span></span>](how-to-create-a-registry-key-and-set-its-value.md)  
 <span data-ttu-id="2bcea-109">描述如何使用 `My.Computer.Registry` 物件的 `CreateSubKey` 和 `SetValue` 方法來建立登錄機碼，並設定其值。</span><span class="sxs-lookup"><span data-stu-id="2bcea-109">Describes how to use the `CreateSubKey` and `SetValue` methods of the `My.Computer.Registry` object to create a registry key and set its value.</span></span>  
  
 [<span data-ttu-id="2bcea-110">作法：讀取登錄機碼的值</span><span class="sxs-lookup"><span data-stu-id="2bcea-110">How to: Read a Value from a Registry Key</span></span>](how-to-read-a-value-from-a-registry-key.md)  
 <span data-ttu-id="2bcea-111">描述如何使用 `My.Computer.Registry` 物件的 `GetValue` 方法來讀取登錄機碼中的值。</span><span class="sxs-lookup"><span data-stu-id="2bcea-111">Describes how to use the `GetValue` method of the `My.Computer.Registry` object to read a value from a registry key.</span></span>  
  
 [<span data-ttu-id="2bcea-112">作法：刪除登錄機碼</span><span class="sxs-lookup"><span data-stu-id="2bcea-112">How to: Delete a Registry Key</span></span>](how-to-delete-a-registry-key.md)  
 <span data-ttu-id="2bcea-113">描述如何使用 `My.Computer.Registry.CurrentUser` 屬性的 `DeleteSubKey` 方法來刪除登錄機碼。</span><span class="sxs-lookup"><span data-stu-id="2bcea-113">Describes how to use the `DeleteSubKey` method of the `My.Computer.Registry.CurrentUser` property to delete a registry key.</span></span>  
  
 [<span data-ttu-id="2bcea-114">使用 Microsoft.Win32 命名空間讀取和寫入登錄</span><span class="sxs-lookup"><span data-stu-id="2bcea-114">Reading from and Writing to the Registry Using the Microsoft.Win32 Namespace</span></span>](reading-from-and-writing-to-the-registry-using-the-microsoft-win32-namespace.md)  
 <span data-ttu-id="2bcea-115">描述如何使用 .NET Framework 的 `Registry` 和 `RegistryKey` 類別來存取登錄。</span><span class="sxs-lookup"><span data-stu-id="2bcea-115">Describes how to use the `Registry` and `RegistryKey` classes of the .NET Framework to access the registry.</span></span>  
  
 [<span data-ttu-id="2bcea-116">安全性和登錄</span><span class="sxs-lookup"><span data-stu-id="2bcea-116">Security and the Registry</span></span>](security-and-the-registry.md)  
 <span data-ttu-id="2bcea-117">討論與登錄有關的安全性問題。</span><span class="sxs-lookup"><span data-stu-id="2bcea-117">Discusses security issues involving the registry.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="2bcea-118">相關章節</span><span class="sxs-lookup"><span data-stu-id="2bcea-118">Related Sections</span></span>  

 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>  
 <span data-ttu-id="2bcea-119">列出並說明 `My.Computer.Registry` 物件的成員。</span><span class="sxs-lookup"><span data-stu-id="2bcea-119">Lists and explains members of the `My.Computer.Registry` object.</span></span>  
  
 <xref:Microsoft.Win32.Registry>  
 <span data-ttu-id="2bcea-120">概述 `Registry` 類別，以及個別索引鍵和成員的連結。</span><span class="sxs-lookup"><span data-stu-id="2bcea-120">Presents an overview of the `Registry` class, along with links to individual keys and members.</span></span>
