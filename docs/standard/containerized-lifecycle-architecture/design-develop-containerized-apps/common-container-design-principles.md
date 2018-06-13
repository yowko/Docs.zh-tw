---
title: 通用容器的設計原則
description: Microsoft 平台和工具的容器化 Docker 應用程式生命週期
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: c67986b1deb504f2b05f2903a263bf1a91f70b08
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33568117"
---
# <a name="common-container-design-principles"></a>通用容器的設計原則

繼續在開發程序而進入 there are 值得一提的是關於如何使用容器的某些基本概念。

## <a name="container-equals-a-process"></a>容器等於處理程序

在容器的模型中，容器會代表單一處理程序。 藉由定義容器做為處理序界限，開始建立用於小數位數，或關閉批次、 程序的基本類型。 當您執行 Docker 容器時，您會看到[ENTRYPOINT](https://docs.docker.com/engine/reference/builder/#/entrypoint)定義。 這會定義處理程序和容器的存留期。 當處理程序完成時，容器的生命週期結束。 有長時間執行的程序，例如 web 伺服器和存留較短的程序，例如批次作業，可能會為 Microsoft Azure 實作[WebJobs](https://azure.microsoft.com/en-us/documentation/articles/websites-webjobs-resources/)。 如果處理序失敗，容器會結束並由 Orchestrator 接管。 如果 orchestrator 已指示要保留五個執行個體執行，而其中一個作業失敗，orchestrator 將會建立另一個容器，以取代失敗的處理序。 在批次工作中，處理序是透過參數來啟動。 當處理序完成時，工作即告完成。

您可能會發現您想要在單一容器中執行的多個處理序的案例。 在任何架構文件，都不會 」 絕不會"也不會有一定的 「 永遠 」。 需要多個處理序的情況下，常見的模式是使用[監督員](http://supervisord.org/)。


>[!div class="step-by-step"]
[上一個] (設計-docker-applications.md) [下一步] (龐大 applications.md)
