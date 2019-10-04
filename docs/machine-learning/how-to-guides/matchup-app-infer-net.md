---
title: 使用 Infer.NET 與概率程式設計建立遊戲配對清單應用程式
description: 了解如何使用 Infer.NET 進行概率程式設計，以 TrueSkill 的簡化版本為基礎，建立遊戲配對清單應用程式。
ms.date: 05/06/2019
ms.custom: mvc,how-to
ms.openlocfilehash: f6f91aecfe7fdeffb7e8913309046c7942ecbab7
ms.sourcegitcommit: 7bfe1682d9368cf88d43e895d1e80ba2d88c3a99
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2019
ms.locfileid: "71957205"
---
# <a name="create-a-game-match-up-list-app-with-infernet-and-probabilistic-programming"></a><span data-ttu-id="a5a33-103">使用 Infer.NET 與概率程式設計建立遊戲配對清單應用程式</span><span class="sxs-lookup"><span data-stu-id="a5a33-103">Create a game match up list app with Infer.NET and probabilistic programming</span></span>

<span data-ttu-id="a5a33-104">本操作指南將教導您如何使用 Infer.NET 進行概率程式設計。</span><span class="sxs-lookup"><span data-stu-id="a5a33-104">This how-to guide teaches you about probabilistic programming using Infer.NET.</span></span> <span data-ttu-id="a5a33-105">概率程式設計是一種機器學習方法，其中自訂模型會以電腦程式表示。</span><span class="sxs-lookup"><span data-stu-id="a5a33-105">Probabilistic programming is a machine learning approach where custom models are expressed as computer programs.</span></span> <span data-ttu-id="a5a33-106">它可將網域知識融入模型中，使機器學習系統更具可解譯性。</span><span class="sxs-lookup"><span data-stu-id="a5a33-106">It allows for incorporating domain knowledge in the models and makes the machine learning system more interpretable.</span></span> <span data-ttu-id="a5a33-107">它也支援線上推斷 - 也就是隨著新資料的到來而學習的程序。</span><span class="sxs-lookup"><span data-stu-id="a5a33-107">It also supports online inference – the process of learning as new data arrives.</span></span> <span data-ttu-id="a5a33-108">Microsoft 的 Azure、Xbox 和 Bing 中的各種產品，都使用 Infer.NET。</span><span class="sxs-lookup"><span data-stu-id="a5a33-108">Infer.NET is used in various products at Microsoft in Azure, Xbox, and Bing.</span></span>

## <a name="what-is-probabilistic-programming"></a><span data-ttu-id="a5a33-109">什麼是概率程式設計？</span><span class="sxs-lookup"><span data-stu-id="a5a33-109">What is probabilistic programming?</span></span>

<span data-ttu-id="a5a33-110">概率程式設計可讓您建立真實世界處理的統計模型。</span><span class="sxs-lookup"><span data-stu-id="a5a33-110">Probabilistic programming allows you to create statistical models of real-world processes.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a5a33-111">必要條件</span><span class="sxs-lookup"><span data-stu-id="a5a33-111">Prerequisites</span></span>

- <span data-ttu-id="a5a33-112">本機開發環境設定</span><span class="sxs-lookup"><span data-stu-id="a5a33-112">Local development environment setup</span></span>

  <span data-ttu-id="a5a33-113">本操作指南需要您具備可用於開發的電腦。</span><span class="sxs-lookup"><span data-stu-id="a5a33-113">This how-to guide expects you to have a machine you can use for development.</span></span> <span data-ttu-id="a5a33-114">.NET 教學課程[Hello World 在10分鐘內](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro)，有在 MacOS、Windows 或 Linux 上設定本機開發環境的指示。</span><span class="sxs-lookup"><span data-stu-id="a5a33-114">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on macOS, Windows, or Linux.</span></span>

## <a name="create-your-app"></a><span data-ttu-id="a5a33-115">建立應用程式</span><span class="sxs-lookup"><span data-stu-id="a5a33-115">Create your app</span></span>

1. <span data-ttu-id="a5a33-116">開啟新的命令提示字元，然後執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="a5a33-116">Open a new command prompt and run the following commands:</span></span>

```dotnetcli
dotnet new console -o myApp
cd myApp
```

<span data-ttu-id="a5a33-117">`dotnet` 命令會建立類型為 `console` 的 `new` 應用程式。</span><span class="sxs-lookup"><span data-stu-id="a5a33-117">The `dotnet` command creates a `new` application of type `console`.</span></span> <span data-ttu-id="a5a33-118">`-o` 參數會建立名為 `myApp` 的目錄，其中會儲存您的應用程式，並填入必要的檔案。</span><span class="sxs-lookup"><span data-stu-id="a5a33-118">The `-o` parameter creates a directory named `myApp` where your app is stored and populates it with the required files.</span></span> <span data-ttu-id="a5a33-119">`cd myApp` 命令會將您帶入新建立的應用程式目錄。</span><span class="sxs-lookup"><span data-stu-id="a5a33-119">The `cd myApp` command puts you into the newly created app directory.</span></span>

## <a name="install-infernet-package"></a><span data-ttu-id="a5a33-120">安裝 Infer.NET 套件</span><span class="sxs-lookup"><span data-stu-id="a5a33-120">Install Infer.NET package</span></span>

<span data-ttu-id="a5a33-121">若要使用 Infer.NET，您需要安裝 `Microsoft.ML.Probabilistic.Compiler` 套件。</span><span class="sxs-lookup"><span data-stu-id="a5a33-121">To use Infer.NET, you need to install the `Microsoft.ML.Probabilistic.Compiler` package.</span></span> <span data-ttu-id="a5a33-122">在命令提示字元中，執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="a5a33-122">In your command prompt, run the following command:</span></span>

```dotnetcli
dotnet add package Microsoft.ML.Probabilistic.Compiler
```

## <a name="design-your-model"></a><span data-ttu-id="a5a33-123">設計您的模型</span><span class="sxs-lookup"><span data-stu-id="a5a33-123">Design your model</span></span>

<span data-ttu-id="a5a33-124">使用在辦公室玩的乒乓球或桌上足球比賽作為範例。</span><span class="sxs-lookup"><span data-stu-id="a5a33-124">The example sample uses table tennis or foosball matches played in the office.</span></span> <span data-ttu-id="a5a33-125">您有每場比賽的參賽者和結果。</span><span class="sxs-lookup"><span data-stu-id="a5a33-125">You have the participants and outcome of each match.</span></span>  <span data-ttu-id="a5a33-126">您想從此資料中推斷出玩家的技巧。</span><span class="sxs-lookup"><span data-stu-id="a5a33-126">You want to infer the player's skills from this data.</span></span> <span data-ttu-id="a5a33-127">假設每位玩家有常態分佈的潛在技巧，並且他們在指定比賽中的表現是該技巧的嘈雜版本。</span><span class="sxs-lookup"><span data-stu-id="a5a33-127">Assume that each player has a normally distributed latent skill and their given match performance is a noisy version of this skill.</span></span> <span data-ttu-id="a5a33-128">資料限制為優勝者的表現大於失敗者的表現。</span><span class="sxs-lookup"><span data-stu-id="a5a33-128">The data constrains the winner’s performance to be greater than the loser’s performance.</span></span> <span data-ttu-id="a5a33-129">這是熱門 [TrueSkill](https://www.microsoft.com/en-us/research/project/trueskill-ranking-system/) 模型的簡化版本，它還支援組隊、抽籤，與其他延伸用途。</span><span class="sxs-lookup"><span data-stu-id="a5a33-129">This is a simplified version of the popular [TrueSkill](https://www.microsoft.com/en-us/research/project/trueskill-ranking-system/) model, which also supports teams, draws, and other extensions.</span></span> <span data-ttu-id="a5a33-130">此模型的[進階版本](https://www.microsoft.com/en-us/research/publication/trueskill-2-improved-bayesian-skill-rating-system/)用於暢銷遊戲作品「最後一戰」和「戰爭機器」中的配對。</span><span class="sxs-lookup"><span data-stu-id="a5a33-130">An [advanced version](https://www.microsoft.com/en-us/research/publication/trueskill-2-improved-bayesian-skill-rating-system/) of this model is used for matchmaking in the best-selling game titles Halo and Gears of War.</span></span>

<span data-ttu-id="a5a33-131">您需要列出推斷的玩家技巧，以及他們的差異，也就是技能不確定性的度量。</span><span class="sxs-lookup"><span data-stu-id="a5a33-131">You need to list the inferred player skills, alongside with their variance – the measure of uncertainty around the skills.</span></span>

<span data-ttu-id="a5a33-132">*遊戲結果範例資料*</span><span class="sxs-lookup"><span data-stu-id="a5a33-132">*Game result sample data*</span></span>

<span data-ttu-id="a5a33-133">遊戲</span><span class="sxs-lookup"><span data-stu-id="a5a33-133">Game</span></span> |<span data-ttu-id="a5a33-134">優勝者</span><span class="sxs-lookup"><span data-stu-id="a5a33-134">Winner</span></span> | <span data-ttu-id="a5a33-135">失敗者</span><span class="sxs-lookup"><span data-stu-id="a5a33-135">Loser</span></span>
---------|----------|---------
 <span data-ttu-id="a5a33-136">1</span><span class="sxs-lookup"><span data-stu-id="a5a33-136">1</span></span> | <span data-ttu-id="a5a33-137">玩家 0</span><span class="sxs-lookup"><span data-stu-id="a5a33-137">Player 0</span></span> | <span data-ttu-id="a5a33-138">玩家 1</span><span class="sxs-lookup"><span data-stu-id="a5a33-138">Player 1</span></span>
 <span data-ttu-id="a5a33-139">2</span><span class="sxs-lookup"><span data-stu-id="a5a33-139">2</span></span> | <span data-ttu-id="a5a33-140">玩家 0</span><span class="sxs-lookup"><span data-stu-id="a5a33-140">Player 0</span></span> | <span data-ttu-id="a5a33-141">玩家 3</span><span class="sxs-lookup"><span data-stu-id="a5a33-141">Player 3</span></span>
 <span data-ttu-id="a5a33-142">3</span><span class="sxs-lookup"><span data-stu-id="a5a33-142">3</span></span> | <span data-ttu-id="a5a33-143">玩家 0</span><span class="sxs-lookup"><span data-stu-id="a5a33-143">Player 0</span></span> | <span data-ttu-id="a5a33-144">玩家 4</span><span class="sxs-lookup"><span data-stu-id="a5a33-144">Player 4</span></span>
 <span data-ttu-id="a5a33-145">4</span><span class="sxs-lookup"><span data-stu-id="a5a33-145">4</span></span> | <span data-ttu-id="a5a33-146">玩家 1</span><span class="sxs-lookup"><span data-stu-id="a5a33-146">Player 1</span></span> | <span data-ttu-id="a5a33-147">玩家 2</span><span class="sxs-lookup"><span data-stu-id="a5a33-147">Player 2</span></span>
 <span data-ttu-id="a5a33-148">5</span><span class="sxs-lookup"><span data-stu-id="a5a33-148">5</span></span> | <span data-ttu-id="a5a33-149">玩家 3</span><span class="sxs-lookup"><span data-stu-id="a5a33-149">Player 3</span></span> | <span data-ttu-id="a5a33-150">玩家 1</span><span class="sxs-lookup"><span data-stu-id="a5a33-150">Player 1</span></span>
 <span data-ttu-id="a5a33-151">6</span><span class="sxs-lookup"><span data-stu-id="a5a33-151">6</span></span> | <span data-ttu-id="a5a33-152">玩家 4</span><span class="sxs-lookup"><span data-stu-id="a5a33-152">Player 4</span></span> | <span data-ttu-id="a5a33-153">玩家 2</span><span class="sxs-lookup"><span data-stu-id="a5a33-153">Player 2</span></span>

<span data-ttu-id="a5a33-154">仔細觀察範例資料，您會發現玩家 3 和 4 都有一次勝利和一次失敗。</span><span class="sxs-lookup"><span data-stu-id="a5a33-154">With a closer look at the sample data, you’ll notice that players 3 and 4 both have one win and one loss.</span></span> <span data-ttu-id="a5a33-155">讓我們看看使用概率程式設計的排名。</span><span class="sxs-lookup"><span data-stu-id="a5a33-155">Let's see what the rankings look like using probabilistic programming.</span></span> <span data-ttu-id="a5a33-156">另請注意，有一位玩家 0，是因為對我們開發人員來說，即使是辦公室配對清單也是從 0 開始編號的。</span><span class="sxs-lookup"><span data-stu-id="a5a33-156">Notice also there is a player zero because even office match up lists are zero based to us developers.</span></span>

## <a name="write-some-code"></a><span data-ttu-id="a5a33-157">撰寫一些程式碼</span><span class="sxs-lookup"><span data-stu-id="a5a33-157">Write some code</span></span>

<span data-ttu-id="a5a33-158">設計完模型後，使用 Infer.NET 模型化 API 將其表示為概率程式。</span><span class="sxs-lookup"><span data-stu-id="a5a33-158">Having designed the model, it’s time to express it as a probabilistic program using the Infer.NET modeling API.</span></span> <span data-ttu-id="a5a33-159">在您慣用的文字編輯器中開啟 `Program.cs`，並使用下列程式碼取代其所有內容：</span><span class="sxs-lookup"><span data-stu-id="a5a33-159">Open `Program.cs` in your favorite text editor and replace all of its contents with the following code:</span></span>

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

## <a name="run-your-app"></a><span data-ttu-id="a5a33-160">執行應用程式</span><span class="sxs-lookup"><span data-stu-id="a5a33-160">Run your app</span></span>

<span data-ttu-id="a5a33-161">在命令提示字元中，執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="a5a33-161">In your command prompt, run the following command:</span></span>

```dotnetcli
dotnet run
```

## <a name="results"></a><span data-ttu-id="a5a33-162">結果</span><span class="sxs-lookup"><span data-stu-id="a5a33-162">Results</span></span>

<span data-ttu-id="a5a33-163">您的結果應該與以下類似：</span><span class="sxs-lookup"><span data-stu-id="a5a33-163">Your results should be similar to the following:</span></span>

```console
Compiling model...done.
Iterating:
.........|.........|.........|.........|.........| 50
Player 0 skill: Gaussian(9.517, 3.926)
Player 3 skill: Gaussian(6.834, 3.892)
Player 4 skill: Gaussian(6.054, 4.731)
Player 1 skill: Gaussian(4.955, 3.503)
Player 2 skill: Gaussian(2.639, 4.288)
```

<span data-ttu-id="a5a33-164">在結果中，請注意，根據我們的模型，玩家 3 的排名略高於玩家 4。</span><span class="sxs-lookup"><span data-stu-id="a5a33-164">In the results, notice that player 3 ranks slightly higher than player 4 according to our model.</span></span> <span data-ttu-id="a5a33-165">這是因為玩家 3 對玩家 1 的勝利，比玩家 4 對玩家 2 的勝利更重要 - 請注意玩家 1 擊敗玩家 2。</span><span class="sxs-lookup"><span data-stu-id="a5a33-165">That’s because the victory of player 3 over player 1 is more significant than the victory of player 4 over player 2 – note that player 1 beats player 2.</span></span> <span data-ttu-id="a5a33-166">玩家 0 是整體冠軍！</span><span class="sxs-lookup"><span data-stu-id="a5a33-166">Player 0 is the overall champ!</span></span>

## <a name="keep-learning"></a><span data-ttu-id="a5a33-167">持續學習</span><span class="sxs-lookup"><span data-stu-id="a5a33-167">Keep learning</span></span>

<span data-ttu-id="a5a33-168">設計統計模型本身就是一項技能。</span><span class="sxs-lookup"><span data-stu-id="a5a33-168">Designing statistical models is a skill on its own.</span></span> <span data-ttu-id="a5a33-169">Microsoft 研究劍橋團隊撰寫了一本[免費線上書籍](http://mbmlbook.com/) \(英文\)，該書對該文章進行了初步介紹。</span><span class="sxs-lookup"><span data-stu-id="a5a33-169">The Microsoft Research Cambridge team has written a [free online book](http://mbmlbook.com/), which gives a gentle introduction to the article.</span></span> <span data-ttu-id="a5a33-170">該書的第 3 章更詳細地介紹了 TrueSkill 模型。</span><span class="sxs-lookup"><span data-stu-id="a5a33-170">Chapter 3 of this book covers the TrueSkill model in more detail.</span></span> <span data-ttu-id="a5a33-171">一旦您在心中有一個模型，就可以使用 Infer.NET 網站上的[詳盡文件](https://dotnet.github.io/infer/) \(英文\) 將其轉換成程式碼。</span><span class="sxs-lookup"><span data-stu-id="a5a33-171">Once you have a model in mind, you can transform it into code using the [extensive documentation](https://dotnet.github.io/infer/) on the Infer.NET website.</span></span>

## <a name="next-steps"></a><span data-ttu-id="a5a33-172">後續步驟</span><span class="sxs-lookup"><span data-stu-id="a5a33-172">Next steps</span></span>

<span data-ttu-id="a5a33-173">請查看 Infer.NET GitHub 存放庫來繼續學習及尋找更多範例。</span><span class="sxs-lookup"><span data-stu-id="a5a33-173">Check out the Infer.NET GitHub repository to continue learning and find more samples.</span></span>
> [!div class="nextstepaction"]
> <span data-ttu-id="a5a33-174">[dotnet/infer GitHub 存放庫](https://github.com/dotnet/infer) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="a5a33-174">[dotnet/infer GitHub repository](https://github.com/dotnet/infer)</span></span>
