---
title: 用戶端偵錯
ms.date: 03/30/2017
ms.assetid: 56f9ad05-ea1b-4ef6-85f2-890f7ed71567
ms.openlocfilehash: 21598b84d0d493bad29a77adf31b85f4989afdc7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61912597"
---
# <a name="debugging-on-the-client"></a><span data-ttu-id="37737-102">用戶端偵錯</span><span class="sxs-lookup"><span data-stu-id="37737-102">Debugging on the Client</span></span>
<span data-ttu-id="37737-103">若要讓使用者更輕鬆地撰寫您的 WCF 服務的用戶端應用程式，您可以加入[ \<serviceDebug >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md)服務行為加入您的服務組態檔。</span><span class="sxs-lookup"><span data-stu-id="37737-103">To make it easier for users to write client applications for your WCF service, you can add the [\<serviceDebug>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) service behavior to the configuration file of your service.</span></span> <span data-ttu-id="37737-104">這個行為可以用來發行說明頁，並將傳回給用戶端的 SOAP 錯誤詳細資料中的 Managed 例外狀況資訊傳回。</span><span class="sxs-lookup"><span data-stu-id="37737-104">This behavior can be used to publish help pages, and return managed exception information in the details of SOAP faults returned to the client.</span></span>
