---
title: "如何：新增或移除存取控制清單項目"
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
- cpp
helpviewer_keywords:
- ACEs [.NET Framework]
- ACLs [.NET Framework]
- access control entries [.NET Framework]
- I/O [.NET Framework], access control list entries
- access control lists [.NET Framework]
ms.assetid: 53758b39-bd9b-4640-bb04-cad5ed8d0abf
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 988fd354caa5fcc716107087242ead113c9a9939
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-add-or-remove-access-control-list-entries"></a>如何：新增或移除存取控制清單項目
若要在檔案加入或移除存取控制清單 (ACL) 項目，必須從檔案或目錄取得 <xref:System.Security.AccessControl.FileSecurity> 或 <xref:System.Security.AccessControl.DirectorySecurity> 物件、修改，然後套用回到檔案或目錄。  
  
### <a name="to-add-or-remove-an-acl-entry-from-a-file"></a>加入或移除檔案的 ACL 項目  
  
1.  呼叫 <xref:System.IO.File.GetAccessControl%2A> 方法來取得 <xref:System.Security.AccessControl.FileSecurity> 物件，其中包含檔案的目前 ACL 項目。  
  
2.  在 <xref:System.Security.AccessControl.FileSecurity> 步驟 1 中傳回的物件加入或移除 ACL 項目。  
  
3.  傳遞 <xref:System.Security.AccessControl.FileSecurity> 物件給 <xref:System.IO.File.SetAccessControl%2A> 方法，以套用所做的變更。  
  
### <a name="to-add-or-remove-an-acl-entry-from-a-directory"></a>加入或移除目錄的 ACL 項目  
  
1.  呼叫 <xref:System.IO.Directory.GetAccessControl%2A> 方法來取得 <xref:System.Security.AccessControl.DirectorySecurity> 物件，其中包含目錄的目前 ACL 項目。  
  
2.  在步驟 1 中傳回的 <xref:System.Security.AccessControl.DirectorySecurity> 物件加入或移除 ACL 項目。  
  
3.  傳遞 <xref:System.Security.AccessControl.DirectorySecurity> 物件給 <xref:System.IO.Directory.SetAccessControl%2A> 方法，以套用所做的變更。  
  
## <a name="example"></a>範例  
 [!code-cpp[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/cpp/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/cpp/sample.cpp#1)]
 [!code-csharp[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/CS/sample.cs#1)]
 [!code-vb[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/VB/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 您必須提供有效的使用者或群組帳戶，才能執行這個範例。 這個範例會使用 <xref:System.IO.File> 物件；不過，相同的程序也用於 <xref:System.IO.FileInfo>、<xref:System.IO.Directory> 和 <xref:System.IO.DirectoryInfo> 類別。
