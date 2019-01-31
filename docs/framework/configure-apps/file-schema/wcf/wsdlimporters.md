---
title: <wsdlImporters>
ms.date: 03/30/2017
ms.assetid: 270c7f93-eab7-47b6-8b94-ac3f5b7f17e4
ms.openlocfilehash: 81fb25f6a77456608fd3cb0d5e73f67c7f7867c3
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55274569"
---
# <a name="wsdlimporters"></a><span data-ttu-id="8b0ce-101">\<wsdlImporters></span><span class="sxs-lookup"><span data-stu-id="8b0ce-101">\<wsdlImporters></span></span>
<span data-ttu-id="8b0ce-102">此組態項目會指定所有 WSDL 匯入工具，以匯入具有 WS-Policy 附件的 Web 服務描述語言 (WSDL) 1.1 中繼資料。</span><span class="sxs-lookup"><span data-stu-id="8b0ce-102">This configuration element specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span> <span data-ttu-id="8b0ce-103">每個子項目都是 <`wsdlImporter`>，可指定匯入中繼資料的方式，並且將該資訊轉換成表示合約和端點資訊的各種類別。</span><span class="sxs-lookup"><span data-stu-id="8b0ce-103">Each child element is a <`wsdlImporter`> that specifies the way to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="8b0ce-104">它可以選擇性地匯入合約和端點資訊，以及可公開 (Expose) 任何匯入錯誤並接受與匯入和轉換處理有關聯之型別資訊的屬性。</span><span class="sxs-lookup"><span data-stu-id="8b0ce-104">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="8b0ce-105">此外，它也支援匯入繫結資訊，以及可提供存取任何原則文件、WSDL 文件、WSDL 延伸和 XML 結構描述文件的屬性。</span><span class="sxs-lookup"><span data-stu-id="8b0ce-105">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b0ce-106">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8b0ce-106">See also</span></span>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [<span data-ttu-id="8b0ce-107">WCF 用戶端組態</span><span class="sxs-lookup"><span data-stu-id="8b0ce-107">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="8b0ce-108">用戶端</span><span class="sxs-lookup"><span data-stu-id="8b0ce-108">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
