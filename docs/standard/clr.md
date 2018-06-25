---
title: Common Language Runtime (CLR)
ms.custom: updateeachrelease
ms.date: 04/16/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- compiling source code, runtime functionality
- code, execution
- managed data
- runtime
- common language runtime
- metadata, runtime functionality
- .NET Framework, common language runtime
- language compilers
- managed code
- source code execution
- code, runtime functionality
ms.assetid: 059a624e-f7db-4134-ba9f-08b676050482
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 89989b4b7730f4e252dc846377b385cb359dbee1
ms.sourcegitcommit: c217b067985905cb21eafc5dd9a83568d7ff4e45
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/22/2018
ms.locfileid: "36315117"
---
# <a name="common-language-runtime-clr-overview"></a>Common Language Runtime (CLR) 概觀

.NET Framework 提供稱為 Common Language Runtime 的執行階段環境，它能執行程式碼，並提供使程式開發過程更為容易的服務。

編譯器和工具會公開 Common Language Runtime 的功能，並且可以讓您撰寫從這個 Managed 執行環境獲益的程式碼。 以 Runtime 為目標的語言編譯器所開發的程式碼稱為 Managed 程式碼；它可因某些功能而得到改進，例如跨程式語言整合、跨程式語言例外狀況處理 (Exception Handling)、增強的安全性、版本控制和部署支援、元件互動的簡化模型，以及偵錯和設定檔服務。

> [!NOTE]
> 編譯器和工具能夠產生 Common Language Runtime 可以使用的輸出，因為類型系統、中繼資料格式和執行階段環境 (虛擬執行系統) 都是以公用標準 ECMA 通用語言基礎結構規格來定義。 如需詳細資訊，請參閱 [ECMA C# 和通用語言基礎結構規格](https://visualstudio.microsoft.com/license-terms/ecma-c-common-language-infrastructure-standards/)。

若要讓 Runtime 能夠提供服務給 Managed 程式碼，語言編譯器必須發出描述程式碼中型別、成員和參考的中繼資料。 中繼資料是與程式碼一起儲存；每一個可載入的 Common Language Runtime 可移植執行檔 (PE) 都包含中繼資料。 Runtime 使用中繼資料來找出並載入類別、配置記憶體中的執行個體 (Instance)、解析方法引動過程 (Method Invocation)、產生機器碼、強制使用安全性，和設定 Run-Time 內容界限 (Context Boundary)。

Runtime 會自動處理物件配置和管理物件的參考，並在它們不再被使用時將它們釋出。 以這個方式管理存留期 (Lifetime) 的物件稱為 Managed 資料。 記憶體回收排除記憶體流失 (Memory Leak) 和其他常見的程式設計錯誤。 如果您的程式碼為 Managed，您可以在 .NET Framework 應用程式中使用 Managed 資料、Unmanaged 資料或兩者。 由於語言編譯器提供它們自己的型別 (如基本型別)，您可能不一定知道 (或需要知道) 資料是否為 Managed。

Common Language Runtime 使得設計其物件可跨語言互動的元件和應用程式更為容易。 不同語言所撰寫的物件可以彼此通訊，而且它們的行為可以緊密整合。 例如，您可以定義一個類別，並接著使用不同語言從您的原始類別來衍生類別，或呼叫原始類別上的方法。 您也可以傳遞類別的執行個體給不同語言撰寫的類別的方法。 這個跨程式語言整合是可能的，因為以 Runtime 為目標的語言編譯器和工具會使用 Runtime 所定義的一般型別系統，而且它們會遵照 Runtime 的規則來定義新型別，以及建立、使用、保存 (Persist) 和繫結至型別。

所有 Managed 元件都攜帶它們據以建置 (Build) 元件和資源的資訊，做為其中繼資料的一部分。 Runtime 使用這個資訊，確保元件或應用程式擁有其所需的一應俱全的指定版本，使程式碼較不可能因某些不符合的相依性而中斷。 註冊資訊和狀態資料不再儲存於登錄，因為可能難以在其中建立和維護它們。 更確切地說，若您定義的型別資訊 (和它們的相依性) 與程式碼一起儲存為中繼資料，會使元件複寫和移除的工作變得簡單許多。

語言編譯器和工具會以旨在對開發人員有用處而且直覺的方式，公開 Runtime 的功能。 這意謂 Runtime 的一些功能在某個環境中可能比在另一個環境更值得注意。 您如何感受 Runtime 取決於您使用哪一種語言編譯器或工具。 例如，如果您是 Visual Basic 開發人員，您可能注意到，有了 Common Language Runtime 之後，Visual Basic 語言具有比從前更多的物件導向功能。 執行階段具有下列優點：

- 效能改善。

- 易於使用以其他語言開發的元件的能力。

- 類別庫 (Class Library) 提供的擴充式型別。

- 有利於物件導向程式設計的語言功能，例如介面、繼承和多載。

- 支援明確無限制執行緒 (Free Threading)，允許建立具有多執行緒、可擴充的應用程式。

- 支援結構化例外狀況處理。

- 支援自訂屬性。

- 記憶體回收。

- 使用委派，而非會增加型別安全和安全性顧慮的函式指標。 如需委派的詳細資訊，請參閱[一般型別系統](../../docs/standard/base-types/common-type-system.md)。

## <a name="clr-versions"></a>CLR 版本

.NET Framework 的版本號碼不一定對應於它包含的 CLR 版本號碼。 下表顯示這兩個版本號碼如何相互關聯。

|.NET Framework 版本|包含的 CLR 版本|
|----------------------------|--------------------------|
|1.0|1.0|
|1.1|1.1|
|2.0|2.0|
|3.0|2.0|
|3.5|2.0|
|4|4|
|4.5 (包括 4.5.1 和 4.5.2)|4|
|4.6 (包括 4.6.1 和 4.6.2)|4|
|4.7 (包括 4.7.1 和 4.7.2)|4|

## <a name="related-topics"></a>相關主題

|標題|描述|
|-----------|-----------------|
|[Managed 執行程序](managed-execution-process.md)|描述充分利用 Common Language Runtime 所需要的步驟。|
|[自動管理記憶體](automatic-memory-management.md)|說明記憶體回收行程如何配置和釋放記憶體。|
|[.NET Framework 概觀](../framework/get-started/overview.md)|說明重要的 .NET Framework 概念，例如一般型別系統、跨語言互通性 (Interoperability)、Managed 執行、應用程式定義域和組件。|
|[一般類型系統](./base-types/common-type-system.md)|描述型別如何在執行階段中宣告、使用和管理，以支援跨程式語言整合。|

## <a name="see-also"></a>另請參閱

[版本和相依性](../framework/migration-guide/versions-and-dependencies.md)
