---
title: C# 簡介 - 熟悉開發工具
description: 此文章提供您將用來在電腦上開發 C# 與 .NET 應用程式的工具基本簡介。
ms.date: 10/23/2018
ms.openlocfilehash: db0b3228272a17feaa11ec754fa0aa4952a0d1ee
ms.sourcegitcommit: a3db1a9eafca89f95ccf361bc1833b47fbb2bb30
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/04/2019
ms.locfileid: "58920658"
---
# <a name="become-familiar-with-the-net-development-tools"></a>熟悉 .NET 開發工具

在電腦上執行教學課程的第一步是設定開發環境。
.NET 主題[只要 10 分鐘立即上手](https://www.microsoft.com/net/core) \(英文\) 中有關於在 Mac、PC 或 Linux 上設定本機開發環境的指示。

或者，您可以安裝 [.NET Core SDK](https://www.microsoft.com/net/download) \(英文\) 和 [Visual Studio Code](https://code.visualstudio.com/) \(英文\)。

## <a name="basic-application-development-flow"></a>基本應用程式開發流程

您會使用 [`dotnet new`](../../../core/tools/dotnet-new.md) 命令建立應用程式。 此命令會產生應用程式所需的檔案和資產。 C# 教學課程簡介都是使用 `console` 應用程式類型。 一旦您掌握基本概念，就可以擴展到其他應用程式類型。

其他會用到的命令為用來建置可執行檔的 [`dotnet build`](../../../core/tools/dotnet-build.md)，以及用來執行可執行檔的 [`dotnet run`](../../../core/tools/dotnet-run.md)。

## <a name="pick-your-tutorial"></a>挑選教學課程

您可以從下列任何一個教學課程開始：

## [<a name="numbers-in-c"></a>C# 中的數字](numbers-in-csharp-local.md)

在 [C# 中的數字](numbers-in-csharp-local.md)教學課程中，您將會學習電腦儲存數字的方式，以及如何使用不同的數值型別來執行計算。 您將會學習進位的基本概念，以及如何使用 C# 執行數學計算。

此教學課程假設您已完成 [Hello World](hello-world.yml) 課程。

## [<a name="branches-and-loops"></a>分支和迴圈](branches-and-loops-local.md)

[分支和迴圈](branches-and-loops-local.md)教學課程會指導您如何根據儲存在變數中的值選取不同程式碼執行路徑的基本概念。 您將會學習控制流程的基本概念，也就是程式做出決定並選擇不同動作的基礎機制。

此教學課程假設您已完成 [Hello World](hello-world.yml) 與 [C# 中的數字](numbers-in-csharp-local.md)課程。

## [<a name="list-collection"></a>清單集合](arrays-and-collections.md)

[List 集合](arrays-and-collections.md)課程會為您說明可儲存資料序列的「List 集合」類型。 您將會學習如何新增及移除項目、搜尋項目，以及對清單進行排序。 您會探索各種不同的清單。 

此教學課程假設您已完成上述課程。

## [<a name="introduction-to-classes"></a>類別簡介](introduction-to-classes.md)

這個最後的 C# 教學課程簡介只能使用您自己的本機開發環境與 .NET Core 在您的電腦上執行。
您會建置一個主控台應用程式，並了解 C# 語言的基本物件導向功能。
