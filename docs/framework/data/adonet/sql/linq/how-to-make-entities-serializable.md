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
ms.workload: dotnet
ms.openlocfilehash: 7c772d15a3c2a6a6dd70e913c152b3bc0f682654
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-make-entities-serializable"></a><span data-ttu-id="2da70-102">如何：讓實體可序列化</span><span class="sxs-lookup"><span data-stu-id="2da70-102">How to: Make Entities Serializable</span></span>
<span data-ttu-id="2da70-103">在產生程式碼時，您可以讓實體成為可序列化。</span><span class="sxs-lookup"><span data-stu-id="2da70-103">You can make entities serializable when you generate your code.</span></span> <span data-ttu-id="2da70-104">實體類別會使用 <xref:System.Runtime.Serialization.DataContractAttribute> 屬性予以裝飾，而資料行則使用 <xref:System.Runtime.Serialization.DataMemberAttribute> 屬性予以裝飾。</span><span class="sxs-lookup"><span data-stu-id="2da70-104">Entity classes are decorated with the <xref:System.Runtime.Serialization.DataContractAttribute> attribute, and columns with the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute.</span></span>  
  
 <span data-ttu-id="2da70-105">使用 [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] 的開發人員可以使用[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]達到這個目的。</span><span class="sxs-lookup"><span data-stu-id="2da70-105">Developers using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] for this purpose.</span></span>  
  
 <span data-ttu-id="2da70-106">如果您使用 SQLMetal 命令列工具，使用**/serialization**選項與`unidirectional`引數。</span><span class="sxs-lookup"><span data-stu-id="2da70-106">If you are using the SQLMetal command-line tool, use the **/serialization** option with the `unidirectional` argument.</span></span> <span data-ttu-id="2da70-107">如需詳細資訊，請參閱 [SqlMetal.exe (程式碼產生工具)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)。</span><span class="sxs-lookup"><span data-stu-id="2da70-107">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2da70-108">範例</span><span class="sxs-lookup"><span data-stu-id="2da70-108">Example</span></span>  
 <span data-ttu-id="2da70-109">下列 SQLMetal 命令列會產生具有可序列化實體的檔案。</span><span class="sxs-lookup"><span data-stu-id="2da70-109">The following SQLMetal command lines produce files that have serializable entities.</span></span>  
  
```  
sqlmetal /code:nwserializable.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
```  
sqlmetal /code:nwserializable.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
## <a name="see-also"></a><span data-ttu-id="2da70-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="2da70-110">See Also</span></span>  
 [<span data-ttu-id="2da70-111">序列化</span><span class="sxs-lookup"><span data-stu-id="2da70-111">Serialization</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/serialization.md)  
 [<span data-ttu-id="2da70-112">建立物件模型</span><span class="sxs-lookup"><span data-stu-id="2da70-112">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
