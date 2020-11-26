---
title: 用戶端偵錯
ms.date: 03/30/2017
ms.assetid: 56f9ad05-ea1b-4ef6-85f2-890f7ed71567
ms.openlocfilehash: 4fc647bcde3d9aed27a46298be8d863947ba0726
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96243985"
---
# <a name="debugging-on-the-client"></a><span data-ttu-id="efc09-102">用戶端偵錯</span><span class="sxs-lookup"><span data-stu-id="efc09-102">Debugging on the Client</span></span>

<span data-ttu-id="efc09-103">若要讓使用者更輕鬆地為您的 WCF 服務撰寫用戶端應用程式，您可以將 [\<serviceDebug>](../../../configure-apps/file-schema/wcf/servicedebug.md) 服務行為新增至服務的設定檔。</span><span class="sxs-lookup"><span data-stu-id="efc09-103">To make it easier for users to write client applications for your WCF service, you can add the [\<serviceDebug>](../../../configure-apps/file-schema/wcf/servicedebug.md) service behavior to the configuration file of your service.</span></span> <span data-ttu-id="efc09-104">這個行為可以用來發行說明頁，並將傳回給用戶端的 SOAP 錯誤詳細資料中的 Managed 例外狀況資訊傳回。</span><span class="sxs-lookup"><span data-stu-id="efc09-104">This behavior can be used to publish help pages, and return managed exception information in the details of SOAP faults returned to the client.</span></span>
