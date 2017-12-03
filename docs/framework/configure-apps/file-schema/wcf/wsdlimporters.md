---
title: '&lt;wsdlImporters&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 270c7f93-eab7-47b6-8b94-ac3f5b7f17e4
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 08dce1244b59a1755afebeaed16f25f51a9480a8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="ltwsdlimportersgt"></a><span data-ttu-id="659fe-102">&lt;wsdlImporters&gt;</span><span class="sxs-lookup"><span data-stu-id="659fe-102">&lt;wsdlImporters&gt;</span></span>
<span data-ttu-id="659fe-103">此組態項目會指定所有 WSDL 匯入工具，以匯入具有 WS-Policy 附件的 Web 服務描述語言 (WSDL) 1.1 中繼資料。</span><span class="sxs-lookup"><span data-stu-id="659fe-103">This configuration element specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span> <span data-ttu-id="659fe-104">每個子項目都是 <`wsdlImporter`>，可指定匯入中繼資料的方式，並且將該資訊轉換成表示合約和端點資訊的各種類別。</span><span class="sxs-lookup"><span data-stu-id="659fe-104">Each child element is a <`wsdlImporter`> that specifies the way to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="659fe-105">它可以選擇性地匯入合約和端點資訊，以及可公開 (Expose) 任何匯入錯誤並接受與匯入和轉換處理有關聯之型別資訊的屬性。</span><span class="sxs-lookup"><span data-stu-id="659fe-105">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="659fe-106">此外，它也支援匯入繫結資訊，以及可提供存取任何原則文件、WSDL 文件、WSDL 延伸和 XML 結構描述文件的屬性。</span><span class="sxs-lookup"><span data-stu-id="659fe-106">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="659fe-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="659fe-107">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.MetadataElement>  
 <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>  
 <xref:System.ServiceModel.Description.MetadataImporter>  
 <xref:System.ServiceModel.Description.WsdlImporter>  
 [<span data-ttu-id="659fe-108">WCF 用戶端組態</span><span class="sxs-lookup"><span data-stu-id="659fe-108">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [<span data-ttu-id="659fe-109">用戶端</span><span class="sxs-lookup"><span data-stu-id="659fe-109">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
