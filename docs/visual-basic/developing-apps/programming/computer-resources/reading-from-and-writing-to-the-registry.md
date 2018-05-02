---
title: 讀取和寫入登錄 (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My.Computer.Registry object, tasks
- registry [Visual Basic], writing to
- registry [Visual Basic], reading
ms.assetid: a13da106-185b-41d7-b23c-416da65e21e4
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a207b169e267fbcaccd46f7240d81afb3db27a8c
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="reading-from-and-writing-to-the-registry-visual-basic"></a><span data-ttu-id="aff5f-102">讀取和寫入登錄 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aff5f-102">Reading from and Writing to the Registry (Visual Basic)</span></span>
<span data-ttu-id="aff5f-103">本主題描述與登錄建立關聯的工作和概念主題。</span><span class="sxs-lookup"><span data-stu-id="aff5f-103">This topic describes task and conceptual topics that are associated with the registry.</span></span>  
  
 <span data-ttu-id="aff5f-104">在 Visual Basic 中進行程式設計時，您可以選擇透過 Visual Basic 所提供的函式或是 .NET Framework 的登錄類別來存取登錄。</span><span class="sxs-lookup"><span data-stu-id="aff5f-104">When programming in Visual Basic, you can choose to access the registry by means of either the functions provided by Visual Basic or the registry classes of the .NET Framework.</span></span> <span data-ttu-id="aff5f-105">登錄會裝載作業系統的資訊，以及電腦所裝載的應用程式的資訊。</span><span class="sxs-lookup"><span data-stu-id="aff5f-105">The registry hosts information from the operating system as well as information from applications hosted on the machine.</span></span> <span data-ttu-id="aff5f-106">如果允許不適當地存取系統資源或受保護資訊，則使用登錄可能會危及安全性。</span><span class="sxs-lookup"><span data-stu-id="aff5f-106">Working with the registry may compromise security by allowing inappropriate access to system resources or protected information.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="aff5f-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="aff5f-107">In This Section</span></span>  
 [<span data-ttu-id="aff5f-108">如何：建立登錄機碼並設定其值</span><span class="sxs-lookup"><span data-stu-id="aff5f-108">How to: Create a Registry Key and Set Its Value</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-create-a-registry-key-and-set-its-value.md)  
 <span data-ttu-id="aff5f-109">描述如何使用 `My.Computer.Registry` 物件的 `CreateSubKey` 和 `SetValue` 方法來建立登錄機碼，並設定其值。</span><span class="sxs-lookup"><span data-stu-id="aff5f-109">Describes how to use the `CreateSubKey` and `SetValue` methods of the `My.Computer.Registry` object to create a registry key and set its value.</span></span>  
  
 [<span data-ttu-id="aff5f-110">如何：讀取登錄機碼的值</span><span class="sxs-lookup"><span data-stu-id="aff5f-110">How to: Read a Value from a Registry Key</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-read-a-value-from-a-registry-key.md)  
 <span data-ttu-id="aff5f-111">描述如何使用 `My.Computer.Registry` 物件的 `GetValue` 方法來讀取登錄機碼中的值。</span><span class="sxs-lookup"><span data-stu-id="aff5f-111">Describes how to use the `GetValue` method of the `My.Computer.Registry` object to read a value from a registry key.</span></span>  
  
 [<span data-ttu-id="aff5f-112">如何：刪除登錄機碼</span><span class="sxs-lookup"><span data-stu-id="aff5f-112">How to: Delete a Registry Key</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-delete-a-registry-key.md)  
 <span data-ttu-id="aff5f-113">描述如何使用 `My.Computer.Registry.CurrentUser` 屬性的 `DeleteSubKey` 方法來刪除登錄機碼。</span><span class="sxs-lookup"><span data-stu-id="aff5f-113">Describes how to use the `DeleteSubKey` method of the `My.Computer.Registry.CurrentUser` property to delete a registry key.</span></span>  
  
 [<span data-ttu-id="aff5f-114">使用 Microsoft.Win32 命名空間讀取和寫入登錄</span><span class="sxs-lookup"><span data-stu-id="aff5f-114">Reading from and Writing to the Registry Using the Microsoft.Win32 Namespace</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry-using-the-microsoft-win32-namespace.md)  
 <span data-ttu-id="aff5f-115">描述如何使用 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] 的 `Registry` 和 `RegistryKey` 類別來存取登錄。</span><span class="sxs-lookup"><span data-stu-id="aff5f-115">Describes how to use the `Registry` and `RegistryKey` classes of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] to access the registry.</span></span>  
  
 [<span data-ttu-id="aff5f-116">安全性和登錄</span><span class="sxs-lookup"><span data-stu-id="aff5f-116">Security and the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)  
 <span data-ttu-id="aff5f-117">討論與登錄有關的安全性問題。</span><span class="sxs-lookup"><span data-stu-id="aff5f-117">Discusses security issues involving the registry.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="aff5f-118">相關章節</span><span class="sxs-lookup"><span data-stu-id="aff5f-118">Related Sections</span></span>  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>  
 <span data-ttu-id="aff5f-119">列出並說明 `My.Computer.Registry` 物件的成員。</span><span class="sxs-lookup"><span data-stu-id="aff5f-119">Lists and explains members of the `My.Computer.Registry` object.</span></span>  
  
 <xref:Microsoft.Win32.Registry>  
 <span data-ttu-id="aff5f-120">概述 `Registry` 類別，以及個別索引鍵和成員的連結。</span><span class="sxs-lookup"><span data-stu-id="aff5f-120">Presents an overview of the `Registry` class, along with links to individual keys and members.</span></span>
