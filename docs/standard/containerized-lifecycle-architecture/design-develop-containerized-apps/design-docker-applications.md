---
title: 設計 Docker 應用程式
description: 您可以在這裡找到微服務架構深入指南的參考資料，因為本指南並未詳細說明該主題。
ms.date: 02/15/2019
ms.openlocfilehash: 535b6cefb7371014527032972ec27ebfe4b67ebc
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/13/2019
ms.locfileid: "65644695"
---
# <a name="design-docker-applications"></a>設計 Docker 應用程式

第 1 章介紹有關容器和 Docker 的基本概念。 該資訊是您開始所需的基本資訊。 但企業應用程式可能很複雜，且是由多個服務而不是單一服務或容器所組成。 針對這些選擇性使用案例，您必須了解其他設計方法，例如服務導向架構 (SOA)，以及更進階的微服務概念和容器協調流程概念。 本文件的討論範圍並不限於微服務，而是針對任何 Docker 應用程式生命週期，因此不會深入探索微服務架構，因為容器和 Docker 也可能與一般 SOA、背景工作或作業，甚至是整合型應用程式部署方法搭配使用。

**詳細資訊**：若要深入了解企業應程式和微服務架構，請閱讀 [.NET 微服務：容器化 .NET 應用程式的架構](../../microservices-architecture/index.md)指南 (您也可以從 <https://aka.ms/MicroservicesEbook> 下載)。

不過，在開始探討應用程式生命週期和 DevOps 之前，請務必了解您要如何設計及建構應用程式，以及您有哪些設計選擇。

>[!div class="step-by-step"]
>[上一頁](index.md)
>[下一頁](common-container-design-principles.md)
