---
title: HOW TO：新增或移除存取控制清單項目 (僅限 .NET Framework)
ms.date: 01/14/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ACEs [.NET Framework]
- ACLs [.NET Framework]
- access control entries [.NET Framework]
- I/O [.NET Framework], access control list entries
- access control lists [.NET Framework]
ms.assetid: 53758b39-bd9b-4640-bb04-cad5ed8d0abf
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 351d8325cc0fc1a1b551b6d513cad02f1291daab
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59772940"
---
# <a name="how-to-add-or-remove-access-control-list-entries-net-framework-only"></a><span data-ttu-id="82a2b-102">HOW TO：新增或移除存取控制清單項目 (僅限 .NET Framework)</span><span class="sxs-lookup"><span data-stu-id="82a2b-102">How to: Add or remove Access Control List entries (.NET Framework only)</span></span>
<span data-ttu-id="82a2b-103">若要在檔案或目錄加入或移除存取控制清單 (ACL) 項目，請從檔案或目錄取得 <xref:System.Security.AccessControl.FileSecurity> 或 <xref:System.Security.AccessControl.DirectorySecurity> 物件。</span><span class="sxs-lookup"><span data-stu-id="82a2b-103">To add or remove Access Control List (ACL) entries to or from a file or directory, get the <xref:System.Security.AccessControl.FileSecurity> or <xref:System.Security.AccessControl.DirectorySecurity> object from the file or directory.</span></span> <span data-ttu-id="82a2b-104">修改物件，然後將其套回至檔案或目錄。</span><span class="sxs-lookup"><span data-stu-id="82a2b-104">Modify the object, and then apply it back to the file or directory.</span></span>  
  
## <a name="add-or-remove-an-acl-entry-from-a-file"></a><span data-ttu-id="82a2b-105">在檔案加入或移除 ACL 項目</span><span class="sxs-lookup"><span data-stu-id="82a2b-105">Add or remove an ACL entry from a file</span></span>  
  
1. <span data-ttu-id="82a2b-106">呼叫 <xref:System.IO.File.GetAccessControl%2A?displayProperty=nameWithType> 方法來取得 <xref:System.Security.AccessControl.FileSecurity> 物件，其中包含檔案的目前 ACL 項目。</span><span class="sxs-lookup"><span data-stu-id="82a2b-106">Call the <xref:System.IO.File.GetAccessControl%2A?displayProperty=nameWithType> method to get a <xref:System.Security.AccessControl.FileSecurity> object that contains the current ACL entries of a file.</span></span>  
  
2. <span data-ttu-id="82a2b-107">在 <xref:System.Security.AccessControl.FileSecurity> 步驟 1 中傳回的物件加入或移除 ACL 項目。</span><span class="sxs-lookup"><span data-stu-id="82a2b-107">Add or remove ACL entries from the <xref:System.Security.AccessControl.FileSecurity> object returned from step 1.</span></span>  
  
3. <span data-ttu-id="82a2b-108">若要套用變更，請將 <xref:System.Security.AccessControl.FileSecurity> 物件傳遞至 <xref:System.IO.File.SetAccessControl%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="82a2b-108">To apply the changes, pass the <xref:System.Security.AccessControl.FileSecurity> object to the <xref:System.IO.File.SetAccessControl%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="add-or-remove-an-acl-entry-from-a-directory"></a><span data-ttu-id="82a2b-109">在目錄加入或移除 ACL 項目</span><span class="sxs-lookup"><span data-stu-id="82a2b-109">Add or remove an ACL entry from a directory</span></span>  
  
1. <span data-ttu-id="82a2b-110">呼叫 <xref:System.IO.Directory.GetAccessControl%2A?displayProperty=nameWithType> 方法來取得 <xref:System.Security.AccessControl.DirectorySecurity> 物件，其中包含目錄的目前 ACL 項目。</span><span class="sxs-lookup"><span data-stu-id="82a2b-110">Call the <xref:System.IO.Directory.GetAccessControl%2A?displayProperty=nameWithType> method to get a <xref:System.Security.AccessControl.DirectorySecurity> object that contains the current ACL entries of a directory.</span></span>  
  
2. <span data-ttu-id="82a2b-111">在 <xref:System.Security.AccessControl.DirectorySecurity> 步驟 1 中傳回的物件加入或移除 ACL 項目。</span><span class="sxs-lookup"><span data-stu-id="82a2b-111">Add or remove ACL entries from the <xref:System.Security.AccessControl.DirectorySecurity> object returned from step 1.</span></span>  
  
3. <span data-ttu-id="82a2b-112">若要套用變更，請將 <xref:System.Security.AccessControl.DirectorySecurity> 物件傳遞至 <xref:System.IO.Directory.SetAccessControl%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="82a2b-112">To apply the changes, pass the <xref:System.Security.AccessControl.DirectorySecurity> object to the <xref:System.IO.Directory.SetAccessControl%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="82a2b-113">範例</span><span class="sxs-lookup"><span data-stu-id="82a2b-113">Example</span></span>  
 <span data-ttu-id="82a2b-114">您必須使用有效的使用者或群組帳戶，才能執行這個範例。</span><span class="sxs-lookup"><span data-stu-id="82a2b-114">You must use a valid user or group account to run this example.</span></span> <span data-ttu-id="82a2b-115">此範例使用 <xref:System.IO.File> 物件。</span><span class="sxs-lookup"><span data-stu-id="82a2b-115">The example uses a <xref:System.IO.File> object.</span></span> <span data-ttu-id="82a2b-116">對 <xref:System.IO.FileInfo>、<xref:System.IO.Directory> 和 <xref:System.IO.DirectoryInfo> 類別使用相同程序。</span><span class="sxs-lookup"><span data-stu-id="82a2b-116">Use the same procedure for the <xref:System.IO.FileInfo>, <xref:System.IO.Directory>, and <xref:System.IO.DirectoryInfo> classes.</span></span>

 [!code-csharp[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/CS/sample.cs#1)]
 [!code-vb[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/VB/sample.vb#1)]  
