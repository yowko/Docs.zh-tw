---
title: "中繼資料格式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: baad1e68-28fc-4a6a-8a43-75e47e7fa871
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d250b57282d24780dcdd1e045f18d7528bd86a90
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="metadata-formats"></a><span data-ttu-id="57ca1-102">中繼資料格式</span><span class="sxs-lookup"><span data-stu-id="57ca1-102">Metadata Formats</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="57ca1-103"> 支援下表中的中繼資料格式。</span><span class="sxs-lookup"><span data-stu-id="57ca1-103"> supports the metadata formats in the following table.</span></span>  
  
## <a name="metadata-specifications-and-usage"></a><span data-ttu-id="57ca1-104">中繼資料規格和用法</span><span class="sxs-lookup"><span data-stu-id="57ca1-104">Metadata Specifications and Usage</span></span>  
  
|<span data-ttu-id="57ca1-105">通訊協定</span><span class="sxs-lookup"><span data-stu-id="57ca1-105">Protocol</span></span>|<span data-ttu-id="57ca1-106">規格和用法</span><span class="sxs-lookup"><span data-stu-id="57ca1-106">Specification and usage</span></span>|  
|--------------|-----------------------------|  
|<span data-ttu-id="57ca1-107">WSDL 1.1</span><span class="sxs-lookup"><span data-stu-id="57ca1-107">WSDL 1.1</span></span>|[<span data-ttu-id="57ca1-108">Web 服務描述語言 (WSDL) 1.1</span><span class="sxs-lookup"><span data-stu-id="57ca1-108">Web Services Description Language (WSDL) 1.1</span></span>](http://go.microsoft.com/fwlink/?LinkId=94859)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="57ca1-109"> 使用 Web 服務描述語言 (WSDL) 來描述服務。</span><span class="sxs-lookup"><span data-stu-id="57ca1-109"> uses Web Services Description Language (WSDL) to describe services.</span></span>|  
|<span data-ttu-id="57ca1-110">XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="57ca1-110">XML Schema</span></span>|<span data-ttu-id="57ca1-111">[XML 結構描述第 2 部分： 資料類型第二版](http://go.microsoft.com/fwlink/?LinkId=94861)和[XML 結構描述第 1 部分： 結構第二版](http://go.microsoft.com/fwlink/?LinkId=94862)</span><span class="sxs-lookup"><span data-stu-id="57ca1-111">[XML Schema Part 2: Datatypes Second Edition](http://go.microsoft.com/fwlink/?LinkId=94861) and [XML Schema Part 1: Structures Second Edition](http://go.microsoft.com/fwlink/?LinkId=94862)</span></span><br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="57ca1-112"> 使用 XML 結構描述來說明訊息中使用的資料型別。</span><span class="sxs-lookup"><span data-stu-id="57ca1-112"> uses the XML Schema to describe data types used in messages.</span></span>|  
|<span data-ttu-id="57ca1-113">WS 原則</span><span class="sxs-lookup"><span data-stu-id="57ca1-113">WS Policy</span></span>|[<span data-ttu-id="57ca1-114">Web 服務原則 1.2-架構 (Ws-policy)</span><span class="sxs-lookup"><span data-stu-id="57ca1-114">Web Services Policy 1.2 - Framework (WS-Policy)</span></span>](http://go.microsoft.com/fwlink/?LinkId=94864)<br /><br /> [<span data-ttu-id="57ca1-115">Web 服務原則 1.5-架構</span><span class="sxs-lookup"><span data-stu-id="57ca1-115">Web Services Policy 1.5 - Framework</span></span>](http://go.microsoft.com/fwlink/?LinkId=94865)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="57ca1-116"> 將 WS-Policy 1.2 或 1.5 規格與定義域特定的判斷提示一起使用，以描述服務需求和功能。</span><span class="sxs-lookup"><span data-stu-id="57ca1-116"> uses the WS-Policy 1.2 or 1.5 specifications with domain-specific assertions to describe service requirements and capabilities.</span></span>|  
|<span data-ttu-id="57ca1-117">WS 原則附件</span><span class="sxs-lookup"><span data-stu-id="57ca1-117">WS Policy Attachments</span></span>|[<span data-ttu-id="57ca1-118">Web 服務原則 1.2-附件 (Ws-policyattachment)</span><span class="sxs-lookup"><span data-stu-id="57ca1-118">Web Services Policy 1.2 - Attachment (WS-PolicyAttachment)</span></span>](http://go.microsoft.com/fwlink/?LinkId=94866)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="57ca1-119"> 實作 WS-Policy 附件以便在不同的 WSDL 範圍中附加原則運算式。</span><span class="sxs-lookup"><span data-stu-id="57ca1-119"> implements WS-Policy Attachments to attach policy expressions at various scopes in WSDL.</span></span>|  
|<span data-ttu-id="57ca1-120">WS 中繼資料交換</span><span class="sxs-lookup"><span data-stu-id="57ca1-120">WS Metadata Exchange</span></span>|[<span data-ttu-id="57ca1-121">Web 服務中繼資料交換 (Ws-metadataexchange) 1.1 版</span><span class="sxs-lookup"><span data-stu-id="57ca1-121">Web Services Metadata Exchange (WS-MetadataExchange) version 1.1</span></span>](http://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="57ca1-122"> 實作 WS-MetadataExchange 以擷取 XML 結構描述、WSDL 和 WS-Policy。</span><span class="sxs-lookup"><span data-stu-id="57ca1-122"> implements WS-MetadataExchange to retrieve XML Schema, WSDL, and WS-Policy.</span></span>|  
|<span data-ttu-id="57ca1-123">WSDL 的 WS 定址繫結</span><span class="sxs-lookup"><span data-stu-id="57ca1-123">WS Addressing Binding for WSDL</span></span>|[<span data-ttu-id="57ca1-124">Web 服務定址 1.0-WSDL 繫結</span><span class="sxs-lookup"><span data-stu-id="57ca1-124">Web Services Addressing 1.0 - WSDL Binding</span></span>](http://go.microsoft.com/fwlink/?LinkId=94869)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="57ca1-125"> 實作 WSDL 的 WS-Addressing 繫結，以便將定址資訊附加到 WSDL。</span><span class="sxs-lookup"><span data-stu-id="57ca1-125"> implements WS-Addressing Binding for WSDL to attach addressing information in WSDL.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="57ca1-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="57ca1-126">See Also</span></span>  
 [<span data-ttu-id="57ca1-127">Web 服務系統提供的互通性繫結所支援的通訊協定</span><span class="sxs-lookup"><span data-stu-id="57ca1-127">Web Services Protocols Supported by System-Provided Interoperability Bindings</span></span>](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md)  
 [<span data-ttu-id="57ca1-128">WSDL 和原則</span><span class="sxs-lookup"><span data-stu-id="57ca1-128">WSDL and Policy</span></span>](../../../../docs/framework/wcf/feature-details/wsdl-and-policy.md)
