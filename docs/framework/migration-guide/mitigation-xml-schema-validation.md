---
title: "風險降低：XML 結構描述驗證"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b73dd4f4-f2dc-47a2-9425-3896e92321fb
caps.latest.revision: 7
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 786e2d0d70aaead6d464d262ca43dade8db64a52
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="mitigation-xml-schema-validation"></a>風險降低：XML 結構描述驗證
在 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 中，若使用的複合索引鍵中有一個索引鍵是空的，則 XSD 結構描述驗證會偵測到唯一條件約束違規。  
  
## <a name="impact"></a>影響  
 此變更的影響很小：根據結構描述規格的規定，因使用內含空白索引鍵的複合索引鍵而造成 `xsd:unique` 違規時，會出現結構描述驗證錯誤。  
  
## <a name="mitigation"></a>緩和  
 當複合索引鍵包含一個空白索引鍵時，可設定是否要偵測結構描述驗證錯誤：  
  
-   自目標為 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 的應用程式開始，預設值為啟用結構描述驗證錯誤偵測；但您也可以選擇不使用，如此便不會偵測結構描述驗證錯誤。  
  
-   若應用程式是在 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 上執行，但目標為 [!INCLUDE[net_v452](../../../includes/net-v452-md.md)] 及更舊版，預設值為不偵測結構描述驗證錯誤；但您也可以選擇使用此功能，以偵測結構描述驗證錯誤。  
  
 您可以使用 <xref:System.AppContext> 類別定義 `System.Xml.IgnoreEmptyKeySequences` 參數值，以設定此行為。 由於參數的預設值是 `false` (不忽略空的索引鍵序列)，因此您可以使用下列程式碼，將參數值設為 `true`，讓目標為 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 的應用程式不使用這項行為：  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#1)] [!code-vb[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#1)]  
  
 對於目標為 [!INCLUDE[net_v452](../../../includes/net-v452-md.md)] 及舊版的應用程式，因為參數預設值為 `true` (會忽略空的索引鍵序列)，所以您可以使用下列程式碼，將參數值設為 `false`，以確保包含空白索引鍵的複合索引鍵，不會產生結構描述驗證錯誤。  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#2)] [!code-vb[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#2)]  
  
## <a name="see-also"></a>另請參閱  
 [重定目標變更](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)

