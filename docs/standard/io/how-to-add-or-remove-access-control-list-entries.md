---
title: 如何：只 .NET Framework) 新增或移除存取控制清單專案 (
ms.date: 01/14/2019
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
ms.openlocfilehash: 53daa88b761f46dab26b1c12c73741e880512d8d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95682688"
---
# <a name="how-to-add-or-remove-access-control-list-entries-net-framework-only"></a><span data-ttu-id="aef77-102">如何：只 .NET Framework) 新增或移除存取控制清單專案 (</span><span class="sxs-lookup"><span data-stu-id="aef77-102">How to: Add or remove Access Control List entries (.NET Framework only)</span></span>

<span data-ttu-id="aef77-103">若要在檔案或目錄加入或移除存取控制清單 (ACL) 項目，請從檔案或目錄取得 <xref:System.Security.AccessControl.FileSecurity> 或 <xref:System.Security.AccessControl.DirectorySecurity> 物件。</span><span class="sxs-lookup"><span data-stu-id="aef77-103">To add or remove Access Control List (ACL) entries to or from a file or directory, get the <xref:System.Security.AccessControl.FileSecurity> or <xref:System.Security.AccessControl.DirectorySecurity> object from the file or directory.</span></span> <span data-ttu-id="aef77-104">修改物件，然後將其套回至檔案或目錄。</span><span class="sxs-lookup"><span data-stu-id="aef77-104">Modify the object, and then apply it back to the file or directory.</span></span>  
  
## <a name="add-or-remove-an-acl-entry-from-a-file"></a><span data-ttu-id="aef77-105">在檔案加入或移除 ACL 項目</span><span class="sxs-lookup"><span data-stu-id="aef77-105">Add or remove an ACL entry from a file</span></span>  
  
1. <span data-ttu-id="aef77-106">呼叫 <xref:System.IO.File.GetAccessControl%2A?displayProperty=nameWithType> 方法來取得 <xref:System.Security.AccessControl.FileSecurity> 物件，其中包含檔案的目前 ACL 項目。</span><span class="sxs-lookup"><span data-stu-id="aef77-106">Call the <xref:System.IO.File.GetAccessControl%2A?displayProperty=nameWithType> method to get a <xref:System.Security.AccessControl.FileSecurity> object that contains the current ACL entries of a file.</span></span>  
  
2. <span data-ttu-id="aef77-107">在 <xref:System.Security.AccessControl.FileSecurity> 步驟 1 中傳回的物件加入或移除 ACL 項目。</span><span class="sxs-lookup"><span data-stu-id="aef77-107">Add or remove ACL entries from the <xref:System.Security.AccessControl.FileSecurity> object returned from step 1.</span></span>  
  
3. <span data-ttu-id="aef77-108">若要套用變更，請將 <xref:System.Security.AccessControl.FileSecurity> 物件傳遞至 <xref:System.IO.File.SetAccessControl%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="aef77-108">To apply the changes, pass the <xref:System.Security.AccessControl.FileSecurity> object to the <xref:System.IO.File.SetAccessControl%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="add-or-remove-an-acl-entry-from-a-directory"></a><span data-ttu-id="aef77-109">在目錄加入或移除 ACL 項目</span><span class="sxs-lookup"><span data-stu-id="aef77-109">Add or remove an ACL entry from a directory</span></span>  
  
1. <span data-ttu-id="aef77-110">呼叫 <xref:System.IO.Directory.GetAccessControl%2A?displayProperty=nameWithType> 方法來取得 <xref:System.Security.AccessControl.DirectorySecurity> 物件，其中包含目錄的目前 ACL 項目。</span><span class="sxs-lookup"><span data-stu-id="aef77-110">Call the <xref:System.IO.Directory.GetAccessControl%2A?displayProperty=nameWithType> method to get a <xref:System.Security.AccessControl.DirectorySecurity> object that contains the current ACL entries of a directory.</span></span>  
  
2. <span data-ttu-id="aef77-111">在 <xref:System.Security.AccessControl.DirectorySecurity> 步驟 1 中傳回的物件加入或移除 ACL 項目。</span><span class="sxs-lookup"><span data-stu-id="aef77-111">Add or remove ACL entries from the <xref:System.Security.AccessControl.DirectorySecurity> object returned from step 1.</span></span>  
  
3. <span data-ttu-id="aef77-112">若要套用變更，請將 <xref:System.Security.AccessControl.DirectorySecurity> 物件傳遞至 <xref:System.IO.Directory.SetAccessControl%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="aef77-112">To apply the changes, pass the <xref:System.Security.AccessControl.DirectorySecurity> object to the <xref:System.IO.Directory.SetAccessControl%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aef77-113">範例</span><span class="sxs-lookup"><span data-stu-id="aef77-113">Example</span></span>  

 <span data-ttu-id="aef77-114">您必須使用有效的使用者或群組帳戶，才能執行這個範例。</span><span class="sxs-lookup"><span data-stu-id="aef77-114">You must use a valid user or group account to run this example.</span></span> <span data-ttu-id="aef77-115">此範例使用 <xref:System.IO.File> 物件。</span><span class="sxs-lookup"><span data-stu-id="aef77-115">The example uses a <xref:System.IO.File> object.</span></span> <span data-ttu-id="aef77-116">對 <xref:System.IO.FileInfo>、<xref:System.IO.Directory> 和 <xref:System.IO.DirectoryInfo> 類別使用相同程序。</span><span class="sxs-lookup"><span data-stu-id="aef77-116">Use the same procedure for the <xref:System.IO.FileInfo>, <xref:System.IO.Directory>, and <xref:System.IO.DirectoryInfo> classes.</span></span>

 [!code-csharp[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/CS/sample.cs#1)]
 [!code-vb[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/VB/sample.vb#1)]  
