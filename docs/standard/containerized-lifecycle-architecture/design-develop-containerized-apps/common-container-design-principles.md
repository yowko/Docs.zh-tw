---
title: 一般容器設計原則
description: Microsoft 平台和工具的容器化 Docker 應用程式生命週期
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 3af174279e8b6f56a10413817b05ef68cfcabea5
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2018
ms.locfileid: "50202170"
---
# <a name="common-container-design-principles"></a>一般容器設計原則

直接的放在開發程序有一些值得一提的是關於您如何使用容器的基本概念。

## <a name="container-equals-a-process"></a>容器等於處理序

在容器模型中，容器代表單一處理序。 藉由定義做為處理序界限的容器，您開始建立用來擴展，或批次關閉時，處理程序的基本項目。 當您執行 Docker 容器時，您會看到[ENTRYPOINT](https://docs.docker.com/engine/reference/builder/#/entrypoint)定義。 這會定義程序和容器的存留期。 此程序完成時，容器的生命週期結束。 有長時間執行的程序，例如 web 伺服器，以及存留較短的程序，例如批次作業，可能會實作為 Microsoft Azure [WebJobs](https://azure.microsoft.com/documentation/articles/websites-webjobs-resources/)。 如果處理序失敗，容器會結束並由 Orchestrator 接管。 如果 orchestrator 已指示要保留五個執行個體執行，且其中一個失敗，協調器會建立另一個容器，來取代失敗的程序。 在批次工作中，處理序是透過參數來啟動。 當處理序完成時，工作即告完成。

您可能會發現您想要在單一容器中執行的多個處理序的案例。 在任何架構文件中，沒有永遠不會 」 永不，"，也不會有一個 「 永遠 」。 需要多個處理序的情況下，常見的模式是使用[監督員](http://supervisord.org/)。


>[!div class="step-by-step"]
[上一頁](design-docker-applications.md)
[下一頁](monolithic-applications.md)
