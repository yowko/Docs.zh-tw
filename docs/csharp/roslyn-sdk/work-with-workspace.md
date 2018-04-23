---
title: 使用 .NET Compiler Platform SDK 工作區模型
description: 此概觀可讓您了解用來查詢與管理程式碼之工作區和專案的類型。
author: billwagner
ms.author: wiwagn
ms.date: 10/15/2017
ms.topic: conceptual
ms.prod: .net
ms.devlang: devlang-csharp
ms.custom: mvc
ms.openlocfilehash: c42795346c505f925c0b4cb232325085fa065201
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="work-with-a-workspace"></a>使用工作區

[工作區] 層是執行程式碼分析以及重構整個方案的起點。 在這層內，工作區 API 可協助您將方案中的所有專案資訊都組織成單一物件模型，以讓您直接存取原始程式文字、語法樹狀結構、語意模型和編譯這類編譯器層物件模型，而不需要剖析檔案、設定選項，或管理專案間相依性。 

IDE 這類主機環境為您提供對應至開啟方案的工作區。 只要載入方案檔，也可以在 IDE 外部使用此模型。

## <a name="workspace"></a>工作區

工作區會主動將方案呈現為專案集合，且每個專案都有文件集合。 工作區通常會繫結至在使用者鍵入或管理屬性時不斷變更的主機環境。 

<xref:Microsoft.CodeAnalysis.Workspace> 可以存取方案的目前模型。 主機環境變更時，工作區會引發對應事件，並更新 <xref:Microsoft.CodeAnalysis.Workspace.CurrentSolution?displayProperty=nameWithType> 屬性。 例如，使用者在文字編輯器中鍵入以對應至其中一個來源文件時，工作區會使用事件來發出訊號：方案的整體模型已變更以及已修改的文件。 您接著可以分析新模型的正確性、反白顯示精確度區域，或者對程式碼變更進行建議來回應這些變更。 

您也可以建立獨立工作區，而獨立工作區與主機環境中斷連線，或用於沒有主機環境的應用程式中。

## <a name="solutions-projects-documents"></a>方案, 專案, 文件

雖然每次按下按鍵時都可能變更工作區，但是您可以分開使用方案的模型。 

方案是專案和文件的不可變模型。 這表示可以共用模型，而不鎖定或重複。 從 <xref:Microsoft.CodeAnalysis.Workspace.CurrentSolution?displayProperty=nameWithType> 屬性取得方案執行個體之後，該執行個體將永遠不會變更。 不過，像是語法樹狀結構和編譯，您可以根據現有方案和特定變更來建構新執行個體以修改方案。 若要取得工作區以反映變更，則必須將已變更的方案明確地套用回工作區。

專案是整體不可變方案模型的一部分。 它代表所有原始程式碼文件、剖析和編譯選項，以及組件和專案對專案參考。 在專案中，您可以存取對應編譯，而不需要判斷專案相依性，或是剖析任何原始程式檔。

文件也是整體不可變方案模型的一部分。 文件代表單一原始程式檔，您可以從中存取檔案、語法樹狀結構和語意模型的文字。

下圖呈現工作區與主機環境的關係、工具，以及如何進行編輯。

![包含專案和原始程式檔之工作區不同項目間的關聯性](media/work-with-workspace/workspace-obj-relations.png)

## <a name="summary"></a>總結

Roslyn 會公開一組編譯器 API 和工作區 API，以提供您原始程式碼的豐富資訊，並且使用 C# 和 Visual Basic 語言也完全不失真。  .NET Compiler Platform SDK 可大幅降低建立以程式碼為中心之工具和應用程式的入門障礙。 它在多個領域中創造了許多創新的機會，例如中繼程式設計、程式碼產生和轉換、C# 和 VB 語言的交互使用，以及在網域特定語言中內嵌 C# 和 VB。  
