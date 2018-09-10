---
title: 管理 .NET Core 安裝
description: 使用並存安裝策略，在您的電腦上管理多個 .NET Core SDK 和執行階段版本。
author: leecow
ms.author: wiwagn
ms.date: 08/22/2018
ms.openlocfilehash: 06c3f43e7917efb8fd31898044d8f5d920c2cada
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2018
ms.locfileid: "43485444"
---
# <a name="manage-net-core-installations"></a>管理 .NET Core 安裝

.NET Core 允許多個 SDK 和執行階段版本共存，因此提高建置及執行 .NET Core 應用程式時的版本相依性彈性。 這些安裝和自動版本向前復原行為提供寶貴的優點，但有一個明顯的缺點。 安裝 .NET Core SDK 或 .NET Core 執行階段的更新之後，舊版仍會保留在磁碟上。 隨時間下來，安裝多個版本會增加磁碟使用量。 目前已發行超過 50 個 .NET Core SDK 更新。 您的系統上可能安裝了許多 SDK 和執行階段版本，這些可以加以移除。

## <a name="safe-to-remove"></a>移除是否安全？

[.NET Core 版本選取](selection.md)行為及不同更新之間的 .NET Core 執行階段相容性，可讓您安全地移除舊版。 .NET Core 執行階段更新在主要版本「範圍」內 (例如 1.x 和 2.x) 是相容的。 此外，較新版本的 .NET Core SDK 通常能夠繼續以相容的方式，來建置以舊版執行階段為目標的應用程式。

一般而言，您只需要最新的 SDK，以及您應用程式所需之執行階段的最新修補版本。 保留舊版 SDK 或執行階段版本的執行個體包括維護以 project.json 為基礎的應用程式。  除非您的應用程式有特定理由需要舊版 SDK 或執行階段，否則您可以安全地移除舊版。

移除 .NET Core 的方法會依平台而異，而且在 .NET Core 版本之間已有些變更。 如需移除不再需要之 .NET Core 版本的詳細資訊，請參閱 [.NET Core 文件](../index.md)中的[如何移除 .NET Core 執行階段和 SDK](remove-runtime-sdk-versions.md)。
