---
title: "如何：讓實體可序列化"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a6c5bf6e-064a-4f77-b74c-76b3a5dec309
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 96d8e05fd6ce71536eacd909a831da0e14aa2f3d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-make-entities-serializable"></a>如何：讓實體可序列化
在產生程式碼時，您可以讓實體成為可序列化。 實體類別會使用 <xref:System.Runtime.Serialization.DataContractAttribute> 屬性予以裝飾，而資料行則使用 <xref:System.Runtime.Serialization.DataMemberAttribute> 屬性予以裝飾。  
  
 使用 [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] 的開發人員可以使用[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]達到這個目的。  
  
 如果您使用 SQLMetal 命令列工具，使用**/serialization**選項與`unidirectional`引數。 如需詳細資訊，請參閱 [SqlMetal.exe (程式碼產生工具)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)。  
  
## <a name="example"></a>範例  
 下列 SQLMetal 命令列會產生具有可序列化實體的檔案。  
  
```  
sqlmetal /code:nwserializable.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
```  
sqlmetal /code:nwserializable.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
## <a name="see-also"></a>另請參閱  
 [序列化](../../../../../../docs/framework/data/adonet/sql/linq/serialization.md)  
 [建立物件模型](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
