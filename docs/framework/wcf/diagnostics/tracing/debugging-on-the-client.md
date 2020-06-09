---
title: 用戶端偵錯
ms.date: 03/30/2017
ms.assetid: 56f9ad05-ea1b-4ef6-85f2-890f7ed71567
ms.openlocfilehash: 0330e0954969fbaf798fe3be029b443f0fa219cd
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84589353"
---
# <a name="debugging-on-the-client"></a><span data-ttu-id="941d4-102">用戶端偵錯</span><span class="sxs-lookup"><span data-stu-id="941d4-102">Debugging on the Client</span></span>
<span data-ttu-id="941d4-103">為了讓使用者更容易為您的 WCF 服務撰寫用戶端應用程式，您可以將 [\<serviceDebug>](../../../configure-apps/file-schema/wcf/servicedebug.md) 服務行為新增至服務的設定檔。</span><span class="sxs-lookup"><span data-stu-id="941d4-103">To make it easier for users to write client applications for your WCF service, you can add the [\<serviceDebug>](../../../configure-apps/file-schema/wcf/servicedebug.md) service behavior to the configuration file of your service.</span></span> <span data-ttu-id="941d4-104">這個行為可以用來發行說明頁，並將傳回給用戶端的 SOAP 錯誤詳細資料中的 Managed 例外狀況資訊傳回。</span><span class="sxs-lookup"><span data-stu-id="941d4-104">This behavior can be used to publish help pages, and return managed exception information in the details of SOAP faults returned to the client.</span></span>
