---
title: 擴充中繼資料系統
ms.date: 03/30/2017
helpviewer_keywords:
- extending metadata [WCF]
ms.assetid: 8c6b3b00-61b8-4589-8fa5-546cc33719bf
ms.openlocfilehash: 7ccef0c2b908a8f78249742decd6c46a862e541e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61991298"
---
# <a name="extending-the-metadata-system"></a><span data-ttu-id="f49da-102">擴充中繼資料系統</span><span class="sxs-lookup"><span data-stu-id="f49da-102">Extending the Metadata System</span></span>
<span data-ttu-id="f49da-103">Windows Communication Foundation (WCF) 中繼資料系統是一組類別和介面，代表實作服務應用程式所需的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="f49da-103">The Windows Communication Foundation (WCF) metadata system is a group of classes and interfaces that represent metadata required to implement service-based applications.</span></span> <span data-ttu-id="f49da-104">修改或擴充類別，或是實作和設定介面，即可匯出和匯入自訂中繼資料 (例如 Web 服務描述語言 (WSDL) 擴充功能或自訂 WS-PolicyAttachments 判斷提示)。</span><span class="sxs-lookup"><span data-stu-id="f49da-104">Modify or extend the classes or implement and configure the interfaces to export and import custom metadata such as Web Services Description Language (WSDL) extensions or custom WS-PolicyAttachments assertions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f49da-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="f49da-105">In This Section</span></span>  
 [<span data-ttu-id="f49da-106">匯出 WCF 延伸模組的自訂中繼資料</span><span class="sxs-lookup"><span data-stu-id="f49da-106">Exporting Custom Metadata for a WCF Extension</span></span>](../../../../docs/framework/wcf/extending/exporting-custom-metadata-for-a-wcf-extension.md)  
 <span data-ttu-id="f49da-107">描述如何實作和使用 <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> 介面，將自訂原則判斷提示嵌入 WSDL 文件中。</span><span class="sxs-lookup"><span data-stu-id="f49da-107">Describes how to implement and use the <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> interface to embed custom policy assertions in WSDL documents.</span></span>  
  
 [<span data-ttu-id="f49da-108">匯入 WCF 延伸模組的自訂中繼資料</span><span class="sxs-lookup"><span data-stu-id="f49da-108">Importing Custom Metadata for a WCF Extension</span></span>](../../../../docs/framework/wcf/extending/importing-custom-metadata-for-a-wcf-extension.md)  
 <span data-ttu-id="f49da-109">描述如何實作和使用 <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> 介面，讀取和回應 WSDL 文件中的自訂原則判斷提示。</span><span class="sxs-lookup"><span data-stu-id="f49da-109">Describes how to implement and use the <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> interface to read and respond to custom policy assertions in WSDL documents.</span></span>  
  
 [<span data-ttu-id="f49da-110">發行與擷取自訂繫結上的中繼資料</span><span class="sxs-lookup"><span data-stu-id="f49da-110">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../../docs/framework/wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)  
 <span data-ttu-id="f49da-111">描述如何透過自訂繫結交換中繼資料。</span><span class="sxs-lookup"><span data-stu-id="f49da-111">Describes how to exchange metadata over custom bindings.</span></span>
