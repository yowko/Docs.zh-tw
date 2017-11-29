---
title: "用戶端偵錯"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 56f9ad05-ea1b-4ef6-85f2-890f7ed71567
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 38742bff446a09df5c549a87bd05177d764c63a9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="debugging-on-the-client"></a><span data-ttu-id="3cfdd-102">用戶端偵錯</span><span class="sxs-lookup"><span data-stu-id="3cfdd-102">Debugging on the Client</span></span>
<span data-ttu-id="3cfdd-103">若要讓使用者撰寫的用戶端應用程式更容易您[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]服務，您可以加入[ \<serviceDebug >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md)服務到您的服務組態檔的行為。</span><span class="sxs-lookup"><span data-stu-id="3cfdd-103">To make it easier for users to write client applications for your [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] service, you can add the [\<serviceDebug>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) service behavior to the configuration file of your service.</span></span> <span data-ttu-id="3cfdd-104">這個行為可以用來發行說明頁，並將傳回給用戶端的 SOAP 錯誤詳細資料中的 Managed 例外狀況資訊傳回。</span><span class="sxs-lookup"><span data-stu-id="3cfdd-104">This behavior can be used to publish help pages, and return managed exception information in the details of SOAP faults returned to the client.</span></span>
