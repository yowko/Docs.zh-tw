---
title: 生產環境中的 gRPC-WCF 開發人員的 gRPC
description: 在生產環境中執行 ASP.NET Core gRPC 應用程式
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 2baef7071ab47616a58346cebf131cf0ba89537a
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846661"
---
# <a name="grpc-in-production"></a><span data-ttu-id="c8d62-103">生產環境中的 gRPC</span><span class="sxs-lookup"><span data-stu-id="c8d62-103">gRPC in production</span></span>

<span data-ttu-id="c8d62-104">ASP.NET Core 3.0 應用程式（包括 gRPC 服務）可以在 Windows、Linux 和容器中使用 Docker 和 Kubernetes 等新式平臺來執行。</span><span class="sxs-lookup"><span data-stu-id="c8d62-104">ASP.NET Core 3.0 applications, including gRPC services, can be run on Windows, Linux, and in containers using modern platforms like Docker and Kubernetes.</span></span> <span data-ttu-id="c8d62-105">本章將探索在生產環境中執行 gRPC 服務的各種選項，並查看監視和記錄選項，以確保系統的最佳操作。</span><span class="sxs-lookup"><span data-stu-id="c8d62-105">This chapter will explore the various options for running your gRPC services in production, and look at monitoring and logging options to ensure the optimal operation of systems.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="c8d62-106">[上一頁](encryption.md)
>[下一頁](self-hosted.md)</span><span class="sxs-lookup"><span data-stu-id="c8d62-106">[Previous](encryption.md)
[Next](self-hosted.md)</span></span>
