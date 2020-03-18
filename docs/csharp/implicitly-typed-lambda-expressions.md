---
title: 隱含型別 Lambda 運算式
description: 了解您為何無法使用隱含型別變數宣告來宣告 Lambda 運算式。
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: a3851da9-e018-4389-9922-233db7d0f841
ms.openlocfilehash: ef437ef961210290db4150a8a5cfb70e01aee958
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79145718"
---
# <a name="implicitly-typed-lambda-expressions"></a>隱含型別 Lambda 運算式

您無法使用隱含型別變數宣告來宣告 Lambda 運算式。
它會導致編譯器發生循環邏輯問題。 `var` 宣告會告知編譯器從指派運算子右邊的運算式類型中，查明變數的類型。 Lambda 運算式沒有編譯時期類型，但可轉換成任何相符的委派或運算式類型。 當您將 Lambda 運算式指派給委派或運算式類型的變數時，也就是告知編譯器嘗試將 Lambda 運算式轉換成符合 [指派給] 變數簽章的運算式或委派。 編譯器必須嘗試使指派右邊的項目符合指派左邊的類型。

指派兩邊都無法告知編譯器檢視指派運算子另一邊的物件，並查看我的類型是否相符。

通過閱讀[本文](https://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/type-inference.pdf)（PDF 下載），您可以獲取有關 C# 語言為何指定該行為的更多詳細資訊。
