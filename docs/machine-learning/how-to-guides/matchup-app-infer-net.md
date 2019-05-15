---
title: 使用 Infer.NET 與概率程式設計建立遊戲配對清單應用程式
description: 了解如何使用 Infer.NET 進行概率程式設計，以 TrueSkill 的簡化版本為基礎，建立遊戲配對清單應用程式。
ms.date: 05/06/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 85cb3753ae19e7ca64002eb7c26b44b6f7d41e4f
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211428"
---
# <a name="create-a-game-match-up-list-app-with-infernet-and-probabilistic-programming"></a>使用 Infer.NET 與概率程式設計建立遊戲配對清單應用程式

本操作指南將教導您如何使用 Infer.NET 進行概率程式設計。 概率程式設計是一種機器學習方法，其中自訂模型會以電腦程式表示。 它可將網域知識融入模型中，使機器學習系統更具可解譯性。 它也支援線上推斷 - 也就是隨著新資料的到來而學習的程序。 Microsoft 的 Azure、Xbox 和 Bing 中的各種產品，都使用 Infer.NET。

## <a name="what-is-probabilistic-programming"></a>什麼是概率程式設計？

概率程式設計可讓您建立真實世界處理的統計模型。

## <a name="prerequisites"></a>必要條件

- 本機開發環境設定

  本操作指南需要您具備可用於開發的電腦。 .NET [只要 10 分鐘立即上手](https://www.microsoft.com/net/core) \(英文\) 教學課程中有關於在 Mac、PC 或 Linux 上設定本機開發環境的指示。

## <a name="create-your-app"></a>建立應用程式

1. 開啟新的命令提示字元，然後執行下列命令：

```console
dotnet new console -o myApp
cd myApp
```

`dotnet` 命令會建立類型為 `console` 的 `new` 應用程式。 `-o` 參數會建立名為 `myApp` 的目錄，其中會儲存您的應用程式，並填入必要的檔案。 `cd myApp` 命令會將您帶入新建立的應用程式目錄。

## <a name="install-infernet-package"></a>安裝 Infer.NET 套件

若要使用 Infer.NET，您需要安裝 `Microsoft.ML.Probabilistic.Compiler` 套件。 在命令提示字元中，執行下列命令：

```console
dotnet add package Microsoft.ML.Probabilistic.Compiler
```

## <a name="design-your-model"></a>設計您的模型

使用在辦公室玩的乒乓球或桌上足球比賽作為範例。 您有每場比賽的參賽者和結果。  您想從此資料中推斷出玩家的技巧。 假設每位玩家有常態分佈的潛在技巧，並且他們在指定比賽中的表現是該技巧的嘈雜版本。 資料限制為優勝者的表現大於失敗者的表現。 這是熱門 [TrueSkill](https://www.microsoft.com/en-us/research/project/trueskill-ranking-system/) 模型的簡化版本，它還支援組隊、抽籤，與其他延伸用途。 此模型的[進階版本](https://www.microsoft.com/en-us/research/publication/trueskill-2-improved-bayesian-skill-rating-system/)用於暢銷遊戲作品「最後一戰」和「戰爭機器」中的配對。

您需要列出推斷的玩家技巧，以及他們的差異，也就是技能不確定性的度量。

*遊戲結果範例資料*

遊戲 |優勝者 | 失敗者
---------|----------|---------
 1 | 玩家 0 | 玩家 1
 2 | 玩家 0 | 玩家 3
 3 | 玩家 0 | 玩家 4
 4 | 玩家 1 | 玩家 2
 5 | 玩家 3 | 玩家 1
 6 | 玩家 4 | 玩家 2

仔細觀察範例資料，您會發現玩家 3 和 4 都有一次勝利和一次失敗。 讓我們看看使用概率程式設計的排名。 另請注意，有一位玩家 0，是因為對我們開發人員來說，即使是辦公室配對清單也是從 0 開始編號的。

## <a name="write-some-code"></a>撰寫一些程式碼

設計完模型後，使用 Infer.NET 模型化 API 將其表示為概率程式。 在您慣用的文字編輯器中開啟 `Program.cs`，並使用下列程式碼取代其所有內容：

```csharp
namespace myApp

{
    using System;
    using System.Linq;
    using Microsoft.ML.Probabilistic;
    using Microsoft.ML.Probabilistic.Distributions;
    using Microsoft.ML.Probabilistic.Models;

    class Program
    {

        static void Main(string[] args)
        {
            // The winner and loser in each of 6 samples games
            var winnerData = new[] { 0, 0, 0, 1, 3, 4 };
            var loserData = new[] { 1, 3, 4, 2, 1, 2 };

            // Define the statistical model as a probabilistic program
            var game = new Range(winnerData.Length);
            var player = new Range(winnerData.Concat(loserData).Max() + 1);
            var playerSkills = Variable.Array<double>(player);
            playerSkills[player] = Variable.GaussianFromMeanAndVariance(6, 9).ForEach(player);

            var winners = Variable.Array<int>(game);
            var losers = Variable.Array<int>(game);

            using (Variable.ForEach(game))
            {
                // The player performance is a noisy version of their skill
                var winnerPerformance = Variable.GaussianFromMeanAndVariance(playerSkills[winners[game]], 1.0);
                var loserPerformance = Variable.GaussianFromMeanAndVariance(playerSkills[losers[game]], 1.0);

                // The winner performed better in this game
                Variable.ConstrainTrue(winnerPerformance > loserPerformance);
            }

            // Attach the data to the model
            winners.ObservedValue = winnerData;
            losers.ObservedValue = loserData;

            // Run inference
            var inferenceEngine = new InferenceEngine();
            var inferredSkills = inferenceEngine.Infer<Gaussian[]>(playerSkills);

            // The inferred skills are uncertain, which is captured in their variance
            var orderedPlayerSkills = inferredSkills
               .Select((s, i) => new { Player = i, Skill = s })
               .OrderByDescending(ps => ps.Skill.GetMean());

            foreach (var playerSkill in orderedPlayerSkills)
            {
                Console.WriteLine($"Player {playerSkill.Player} skill: {playerSkill.Skill}");
            }
        }
    }
}
```

## <a name="run-your-app"></a>執行應用程式

在命令提示字元中，執行下列命令：

```console
dotnet run
```

## <a name="results"></a>結果

您的結果應該與以下類似：

```
Compiling model...done.
Iterating:
.........|.........|.........|.........|.........| 50
Player 0 skill: Gaussian(9.517, 3.926)
Player 3 skill: Gaussian(6.834, 3.892)
Player 4 skill: Gaussian(6.054, 4.731)
Player 1 skill: Gaussian(4.955, 3.503)
Player 2 skill: Gaussian(2.639, 4.288)
```

在結果中，請注意，根據我們的模型，玩家 3 的排名略高於玩家 4。 這是因為玩家 3 對玩家 1 的勝利，比玩家 4 對玩家 2 的勝利更重要 - 請注意玩家 1 擊敗玩家 2。 玩家 0 是整體冠軍！

## <a name="keep-learning"></a>持續學習

設計統計模型本身就是一項技能。 Microsoft 研究劍橋團隊撰寫了一本[免費線上書籍](http://mbmlbook.com/) \(英文\)，該書對該文章進行了初步介紹。 該書的第 3 章更詳細地介紹了 TrueSkill 模型。 一旦您在心中有一個模型，就可以使用 Infer.NET 網站上的[詳盡文件](https://dotnet.github.io/infer/) \(英文\) 將其轉換成程式碼。

## <a name="next-steps"></a>後續步驟

請查看 Infer.NET GitHub 存放庫來繼續學習及尋找更多範例。
> [!div class="nextstepaction"]
> [dotnet/infer GitHub 存放庫](https://github.com/dotnet/infer) \(英文\)
