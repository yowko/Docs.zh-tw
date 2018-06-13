---
title: 隱含型別 Lambda 運算式
description: 了解您為何無法使用隱含型別變數宣告來宣告 Lambda 運算式。
ms.date: 06/20/2016
ms.assetid: a3851da9-e018-4389-9922-233db7d0f841
ms.openlocfilehash: f06c55f51c30c941d6d507ac8e2edd95c5152742
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33211819"
---
# <a name="implicitly-typed-lambda-expressions"></a>隱含型別 Lambda 運算式

我將不會使用 `var` 來宣告此運算式樹狀架構。 您無法使用隱含型別變數宣告來宣告 Lambda 運算式。
它會導致編譯器發生循環邏輯問題。 `var` 宣告會告知編譯器從指派運算子右邊的運算式類型中，查明變數的類型。 Lambda 運算式沒有編譯時期類型，但可轉換成任何相符的委派或運算式類型。 當您將 Lambda 運算式指派給委派或運算式類型的變數時，也就是告知編譯器嘗試將 Lambda 運算式轉換成符合 [指派給] 變數簽章的運算式或委派。 編譯器必須嘗試使指派右邊的項目符合指派左邊的類型。 

指派兩邊都無法告知編譯器檢視指派運算子另一邊的物件，並查看我的類型是否相符。

您可以閱讀[這篇文章](http://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/type-inference.pdf) (PDF 下載)，以取得更多有關 C# 語言為什麼會指定該行為的詳細資訊


