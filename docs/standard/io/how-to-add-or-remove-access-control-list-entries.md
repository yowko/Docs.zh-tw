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
ms.openlocfilehash: ea1059f541d2449a1a2d5dca1644ce8d9a553e40
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55283344"
---
# <a name="how-to-add-or-remove-access-control-list-entries-net-framework-only"></a>HOW TO：新增或移除存取控制清單項目 (僅限 .NET Framework)
若要在檔案或目錄加入或移除存取控制清單 (ACL) 項目，請從檔案或目錄取得 <xref:System.Security.AccessControl.FileSecurity> 或 <xref:System.Security.AccessControl.DirectorySecurity> 物件。 修改物件，然後將其套回至檔案或目錄。  
  
## <a name="add-or-remove-an-acl-entry-from-a-file"></a>在檔案加入或移除 ACL 項目  
  
1.  呼叫 <xref:System.IO.File.GetAccessControl%2A?displayProperty=nameWithType> 方法來取得 <xref:System.Security.AccessControl.FileSecurity> 物件，其中包含檔案的目前 ACL 項目。  
  
2.  在步驟 1 中傳回的 <xref:System.Security.AccessControl.FileSecurity> 物件加入或移除 ACL 項目。  
  
3. 若要套用變更，請將 <xref:System.Security.AccessControl.FileSecurity> 物件傳遞至 <xref:System.IO.File.SetAccessControl%2A?displayProperty=nameWithType> 方法。  
  
## <a name="add-or-remove-an-acl-entry-from-a-directory"></a>在目錄加入或移除 ACL 項目  
  
1.  呼叫 <xref:System.IO.Directory.GetAccessControl%2A?displayProperty=nameWithType> 方法來取得 <xref:System.Security.AccessControl.DirectorySecurity> 物件，其中包含目錄的目前 ACL 項目。  
  
2.  在步驟 1 中傳回的 <xref:System.Security.AccessControl.DirectorySecurity> 物件加入或移除 ACL 項目。  
  
3.  若要套用變更，請將 <xref:System.Security.AccessControl.DirectorySecurity> 物件傳遞至 <xref:System.IO.Directory.SetAccessControl%2A?displayProperty=nameWithType> 方法。  
  
## <a name="example"></a>範例  
 您必須使用有效的使用者或群組帳戶，才能執行這個範例。 此範例使用 <xref:System.IO.File> 物件。 對 <xref:System.IO.FileInfo>、<xref:System.IO.Directory> 和 <xref:System.IO.DirectoryInfo> 類別使用相同程序。

 [!code-csharp[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/CS/sample.cs#1)]
 [!code-vb[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/VB/sample.vb#1)]  
  
