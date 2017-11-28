---
title: "在 Windows 10、Windows 8.1 及 Windows 8 上安裝 .NET Framework 3.5"
description: "了解如何在 Windows 10、Windows 8.1 及 Windows 8 上安裝 .NET Framework 3.5。"
author: rlander
ms.author: mairaw
keywords: ".NET Framework, 安裝"
ms.date: 05/26/2017
ms.topic: article
ms.prod: .net-framework
ms.technology: vs-ide-deployment
ms.devlang: dotnet
ms.assetid: 67cda1d5-c6g4-4eb5-93e6-4f478de07ff7
ms.openlocfilehash: 85a3cada074714c24015d90c26d94551f4f411f2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="install-the-net-framework-35-on-windows-10-windows-81-and-windows-8"></a>在 Windows 10、Windows 8.1 及 Windows 8 上安裝 .NET Framework 3.5

您可能需要 .NET Framework 3.5，才能在 Windows 10、Windows 8.1 及 Windows 8 上執行應用程式。 這些指示也適用於較舊的 Windows 版本。

## <a name="install-the-net-framework-35-on-demand"></a>視需要安裝 .NET Framework 3.5

如果您嘗試執行需要 .NET Framework 3.5 的應用程式，可能會看到下列設定對話方塊。 請選擇 [安裝此功能] 來啟用 .NET Framework 3.5。 這個選項需要網際網路連線。

![.NET Framework 安裝對話方塊](./media/dotnet-framework-installation-dialog.jpg)

## <a name="enable-the-net-framework-35-in-control-panel"></a>在控制台中啟用 .NET Framework 3.5

您可以透過 Windows 的 [控制台] 啟用 .NET Framework 3.5。 這個選項需要網際網路連線。

1. 按下鍵盤上的 Windows 鍵 ![Windows 標誌](https://i-msdn.sec.s-msft.com/dynimg/IC721376.jpeg)，鍵入「Windows 功能」，然後按 Enter 鍵。 [開啟或關閉 Windows 功能] 對話方塊隨即出現。

2. 選取 [.NET Framework 3.5 (包括 .NET 2.0 和 3.0)] 核取方塊，選取 [確定]，然後在出現提示時重新啟動電腦。

   ![使用控制台來安裝 .NET](./media/dotnet-control-panel.png)

   您不需要選取 [Windows Communication Foundation (WCF) HTTP 啟用] 和 [Windows Communication Foundation (WCF) 非 HTTP 啟用] 的子項目，除非您是需要這項功能的開發人員或伺服器系統管理員。
