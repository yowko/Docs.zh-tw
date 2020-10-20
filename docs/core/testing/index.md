---
title: 在 .NET 中測試
description: 本文簡要說明在 .NET 中測試的測試概念、術語和工具。
author: IEvangelist
ms.author: dapine
ms.date: 10/19/2020
ms.openlocfilehash: 36e88cc059447a98931593e0535c70cbc92a2cf4
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/20/2020
ms.locfileid: "92223472"
---
# <a name="testing-in-net"></a>在 .NET 中測試

本文介紹測試的概念，並說明如何使用不同類型的測試來驗證程式代碼。 有多種工具可用來測試 .NET 應用程式，例如 [.NET CLI](#net-cli) 或 [整合式開發環境 (ide) ](#ide)。

## <a name="test-types"></a>測試類型

擁有自動化測試是確保應用程式程式碼會執行其作者所要執行之作業的絕佳方式。 本文涵蓋單元測試、整合測試和負載測試。

### <a name="unit-tests"></a>單元測試

*單元測試*是練習個別軟體元件或方法（也稱為「工作單位」）的測試。 單元測試應該只測試開發人員控制項內的程式碼。 它們並不會測試基礎結構的考慮。 基礎結構的考慮包括與資料庫、檔案系統和網路資源的互動。

如需有關建立單元測試的詳細資訊，請參閱 [測試控管](#testing-tools)。

### <a name="integration-tests"></a>整合測試

*整合測試*與單元測試不同之處在于，它會演練兩個或多個軟體元件的功能，也稱為「整合」。 這些測試會在較廣泛的受測系統上運作，而單元測試則著重于個別的元件。 整合測試通常會包含基礎結構考慮。

### <a name="load-tests"></a>負載測試

*負載測試*的目標是要判斷系統是否可以處理指定的負載，例如，使用應用程式的並行使用者數目，以及應用程式處理互動佳的能力。 如需有關 web 應用程式負載測試的詳細資訊，請參閱 [ASP.NET Core 負載/壓力測試](/aspnet/core/test/load-tests)。

## <a name="test-considerations"></a>測試考慮

請記住，有撰寫測試的 [最佳做法](unit-testing-best-practices.md) 。 例如， [測試導向開發 (TDD) ](https://deviq.com/test-driven-development) 就是在要檢查的程式碼之前寫入單元測試。 TDD 就像是在您撰寫書籍之前建立書籍的大綱。 它的目標是協助開發人員撰寫更簡單、更易讀且更有效率的程式碼。

## <a name="testing-tools"></a>測試工具

.Net 是多國語言的開發平臺，您可以撰寫適用于 [c #](../../csharp/index.yml)、 [F #](../../fsharp/index.yml)和 [Visual Basic](../../visual-basic/index.yml)的各種測試類型。 針對上述每一種語言，您可以選擇數個測試架構。

### <a name="xunit"></a>xUnit

[xUnit](https://xunit.net) 是適用于 .net 的免費開放原始碼、以社區為導向的單元測試工具。 XUnit.net 是由 NUnit v2 的原始發明者所撰寫，是適用于 .NET 應用程式單元測試的最新技術。 xUnit.net 適用于 ReSharper、CodeRush、TestDriven.NET 和 [Xamarin](/apps/xamarin)。 它是 [.Net Foundation](https://dotnetfoundation.org) 的專案，並在其管理辦法下運作。

如需詳細資訊，請參閱下列資源：

- [使用 C 的單元測試#](unit-testing-with-dotnet-test.md)
- [使用 F 的單元測試#](unit-testing-fsharp-with-dotnet-test.md)
- [使用 Visual Basic 的單元測試](unit-testing-visual-basic-with-dotnet-test.md)

### <a name="nunit"></a>NUnit

[NUnit](https://nunit.org) 是適用于所有 .net 語言的單元測試架構。 從 JUnit 開始，目前的生產版本已重寫許多新功能，並支援各種不同的 .NET 平臺。 它是 [.Net Foundation](https://dotnetfoundation.org)的專案。

如需詳細資訊，請參閱下列資源：

- [使用 C 的單元測試#](unit-testing-with-nunit.md)
- [使用 F 的單元測試#](unit-testing-fsharp-with-nunit.md)
- [使用 Visual Basic 的單元測試](unit-testing-visual-basic-with-nunit.md)

### <a name="mstest"></a>MSTest

[MSTest](https://github.com/Microsoft/testfx-docs) 是適用于所有 .net 語言的 Microsoft 測試架構。 它是可擴充的，而且可搭配 .NET CLI 和 Visual Studio 使用。 如需詳細資訊，請參閱下列資源：

- [使用 C 的單元測試#](unit-testing-with-mstest.md)
- [使用 F 的單元測試#](unit-testing-fsharp-with-mstest.md)
- [使用 Visual Basic 的單元測試](unit-testing-visual-basic-with-mstest.md)

### <a name="net-cli"></a>.NET CLI

您可以使用[dotnet test](../tools/dotnet-test.md)命令，從[.net CLI](../tools/index.md)執行解決方案單元測試。 .NET CLI [ (ide) ](#ide) 提供的大部分功能，都可透過使用者介面來公開。 .NET CLI 可跨平臺使用，並可作為持續整合和傳遞管線的一部分。 .NET CLI 會與腳本處理常式搭配使用，以將一般工作自動化。

### <a name="ide"></a>IDE

無論您是使用 Visual Studio、Visual Studio for Mac 或 Visual Studio Code，都有用於測試功能的圖形化使用者介面。 Ide 有比 CLI 更多的可用功能，例如 [Live Unit Testing](/visualstudio/test/live-unit-testing)。 如需詳細資訊，請參閱 [包含和排除具有 Visual Studio 的測試](/visualstudio/test/live-unit-testing#include-and-exclude-test-projects-and-test-methods)。

## <a name="see-also"></a>請參閱

如需詳細資訊，請參閱下列文章：

- [使用 .NET 的單元測試最佳做法](unit-testing-best-practices.md)
- [ASP.NET Core 中的整合測試](/aspnet/core/test/integration-tests#test-app-prerequisites)
- [執行選擇性單元測試](selective-unit-tests.md)
- [使用程式碼涵蓋範圍進行單元測試](unit-testing-code-coverage.md)
