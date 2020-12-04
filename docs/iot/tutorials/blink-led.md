---
title: 閃爍 LED
description: 瞭解如何使用 .NET IoT 程式庫來使 LED 閃爍。
author: camsoper
ms.author: casoper
ms.date: 11/13/2020
ms.topic: tutorial
ms.prod: dotnet
ms.openlocfilehash: 07a050c0655f9cae3d7f2b924c0dd07ac1c6c0b9
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96586670"
---
# <a name="blink-an-led"></a><span data-ttu-id="cd61d-103">閃爍 LED</span><span class="sxs-lookup"><span data-stu-id="cd61d-103">Blink an LED</span></span>

<span data-ttu-id="cd61d-104">一般用途的 i/o (GPIO) pin 可以個別控制。</span><span class="sxs-lookup"><span data-stu-id="cd61d-104">General-purpose I/O (GPIO) pins can be controlled individually.</span></span> <span data-ttu-id="cd61d-105">這適用于控制 Led、轉送和其他具狀態裝置。</span><span class="sxs-lookup"><span data-stu-id="cd61d-105">This is useful for controlling LEDs, relays, and other stateful devices.</span></span> <span data-ttu-id="cd61d-106">在本主題中，您將使用 .NET 和 Raspberry Pi 的 GPIO 針腳來開啟 LED 並重複閃爍。</span><span class="sxs-lookup"><span data-stu-id="cd61d-106">In this topic, you will use .NET and your Raspberry Pi's GPIO pins to power an LED and blink it repeatedly.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="cd61d-107">先決條件</span><span class="sxs-lookup"><span data-stu-id="cd61d-107">Prerequisites</span></span>

- [!INCLUDE [prereq-rpi](../includes/prereq-rpi.md)]
- <span data-ttu-id="cd61d-108">5 mm LED</span><span class="sxs-lookup"><span data-stu-id="cd61d-108">5 mm LED</span></span>
- <span data-ttu-id="cd61d-109">330Ω電阻器</span><span class="sxs-lookup"><span data-stu-id="cd61d-109">330 Ω resistor</span></span>
- <span data-ttu-id="cd61d-110">試驗電路板</span><span class="sxs-lookup"><span data-stu-id="cd61d-110">Breadboard</span></span>
- <span data-ttu-id="cd61d-111">跳線</span><span class="sxs-lookup"><span data-stu-id="cd61d-111">Jumper wires</span></span>
- <span data-ttu-id="cd61d-112">Raspberry Pi GPIO (選用/建議) </span><span class="sxs-lookup"><span data-stu-id="cd61d-112">Raspberry Pi GPIO breakout board (optional/recommended)</span></span>
- [!INCLUDE [tutorial-prereq-dotnet](../includes/tutorial-prereq-dotnet.md)]

[!INCLUDE [ensure-ssh](../includes/ensure-ssh.md)]

## <a name="prepare-the-hardware"></a><span data-ttu-id="cd61d-113">準備硬體</span><span class="sxs-lookup"><span data-stu-id="cd61d-113">Prepare the hardware</span></span>

<span data-ttu-id="cd61d-114">使用硬體元件來建立線路，如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="cd61d-114">Use the hardware components to build the circuit as depicted in the following diagram:</span></span>

:::image type="content" source="../media/rpi-led_bb-thumb.png" alt-text="Fritzing 圖顯示具有 LED 和電阻的電路" lightbox="../media/rpi-led_bb.png":::

<span data-ttu-id="cd61d-116">上圖描述下列連接：</span><span class="sxs-lookup"><span data-stu-id="cd61d-116">The image above depicts the following connections:</span></span>

- <span data-ttu-id="cd61d-117">GPIO 18 到 LED 陽極 (更長、正面潛在客戶) </span><span class="sxs-lookup"><span data-stu-id="cd61d-117">GPIO 18 to LED anode (longer, positive lead)</span></span>
- <span data-ttu-id="cd61d-118">領先的陰極 (更短、負面潛在客戶) 至330Ω電阻器 (可能會結束) </span><span class="sxs-lookup"><span data-stu-id="cd61d-118">LED cathode (shorter, negative lead) to 330 Ω resistor (either end)</span></span>
- <span data-ttu-id="cd61d-119">330Ω電阻器 (其他端) 至地面</span><span class="sxs-lookup"><span data-stu-id="cd61d-119">330 Ω resistor (other end) to ground</span></span>

[!INCLUDE [tutorial-rpi-gpio](../includes/tutorial-rpi-gpio.md)]

[!INCLUDE [gpio-breakout](../includes/gpio-breakout.md)]

## <a name="create-the-app"></a><span data-ttu-id="cd61d-120">建立應用程式</span><span class="sxs-lookup"><span data-stu-id="cd61d-120">Create the app</span></span>

<span data-ttu-id="cd61d-121">請在您慣用的開發環境中完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="cd61d-121">Complete the following steps in your preferred development environment:</span></span>

1. <span data-ttu-id="cd61d-122">使用 [.NET CLI](../../core/tools/dotnet-new.md) 或 [Visual Studio](../../core/tutorials/with-visual-studio.md)建立新的 .net 主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="cd61d-122">Create a new .NET Console App using either the [.NET CLI](../../core/tools/dotnet-new.md) or [Visual Studio](../../core/tutorials/with-visual-studio.md).</span></span> <span data-ttu-id="cd61d-123">將它命名為 *BlinkTutorial*。</span><span class="sxs-lookup"><span data-stu-id="cd61d-123">Name it *BlinkTutorial*.</span></span>

    ```dotnetcli
    dotnet new console -o BlinkTutorial
    ```

1. [!INCLUDE [tutorial-add-packages](../includes/tutorial-add-packages.md)]
1. <span data-ttu-id="cd61d-124">使用下列程式碼取代 *Program.cs* 的內容：</span><span class="sxs-lookup"><span data-stu-id="cd61d-124">Replace the contents of *Program.cs* with the following code:</span></span>

    :::code language="csharp" source="~/iot-samples/tutorials/BlinkTutorial/Program.cs" :::

    <span data-ttu-id="cd61d-125">在上述程式碼中：</span><span class="sxs-lookup"><span data-stu-id="cd61d-125">In the preceding code:</span></span>

    - <span data-ttu-id="cd61d-126">[Using](../../csharp/whats-new/csharp-8.md#using-declarations)宣告會建立的實例 `GpioController` 。</span><span class="sxs-lookup"><span data-stu-id="cd61d-126">A [using declaration](../../csharp/whats-new/csharp-8.md#using-declarations) creates an instance of `GpioController`.</span></span> <span data-ttu-id="cd61d-127">宣告 `using` 可確保物件已處置，且硬體資源已正確釋放。</span><span class="sxs-lookup"><span data-stu-id="cd61d-127">The `using` declaration ensures the object is disposed and hardware resources are released properly.</span></span>
    - <span data-ttu-id="cd61d-128">已開啟 GPIO pin 碼18作為輸出</span><span class="sxs-lookup"><span data-stu-id="cd61d-128">GPIO pin 18 is opened for output</span></span>
    - <span data-ttu-id="cd61d-129">`while`迴圈會無限期地執行。</span><span class="sxs-lookup"><span data-stu-id="cd61d-129">A `while` loop runs indefinitely.</span></span> <span data-ttu-id="cd61d-130">每個反復專案：</span><span class="sxs-lookup"><span data-stu-id="cd61d-130">Each iteration:</span></span>
        1. <span data-ttu-id="cd61d-131">將值寫入 GPIO 針腳18。</span><span class="sxs-lookup"><span data-stu-id="cd61d-131">Writes a value to GPIO pin 18.</span></span> <span data-ttu-id="cd61d-132">若 `ledOn` 為 true，則會 `PinValue.High` 在) 寫入 (。</span><span class="sxs-lookup"><span data-stu-id="cd61d-132">If `ledOn` is true, it writes `PinValue.High` (on).</span></span> <span data-ttu-id="cd61d-133">否則，它會寫入 `PinValue.Low` 。</span><span class="sxs-lookup"><span data-stu-id="cd61d-133">Otherwise, it writes `PinValue.Low`.</span></span>
        1. <span data-ttu-id="cd61d-134">睡眠 1000 ms。</span><span class="sxs-lookup"><span data-stu-id="cd61d-134">Sleeps 1000 ms.</span></span>
        1. <span data-ttu-id="cd61d-135">切換的值 `ledOn` 。</span><span class="sxs-lookup"><span data-stu-id="cd61d-135">Toggles the value of `ledOn`.</span></span>

1. [!INCLUDE [tutorial-build](../includes/tutorial-build.md)]
1. [!INCLUDE [tutorial-deploy](../includes/tutorial-deploy.md)]
1. <span data-ttu-id="cd61d-136">切換至部署目錄並執行可執行檔，以在 Raspberry Pi 上執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="cd61d-136">Run the app on the Raspberry Pi by switching to the deployment directory and running the executable.</span></span>

    ```bash
    ./BlinkTutorial
    ```

    <span data-ttu-id="cd61d-137">LED 會在每秒閃爍一次。</span><span class="sxs-lookup"><span data-stu-id="cd61d-137">The LED blinks off and on every second.</span></span>

1. <span data-ttu-id="cd61d-138">按 <kbd>Ctrl + C</kbd>來終止程式。</span><span class="sxs-lookup"><span data-stu-id="cd61d-138">Terminate the program by pressing <kbd>Ctrl+C</kbd>.</span></span>

<span data-ttu-id="cd61d-139">恭喜！</span><span class="sxs-lookup"><span data-stu-id="cd61d-139">Congratulations!</span></span> <span data-ttu-id="cd61d-140">您已使用 GPIO 來使 LED 閃爍。</span><span class="sxs-lookup"><span data-stu-id="cd61d-140">You've used GPIO to blink an LED.</span></span>

## <a name="get-the-source-code"></a><span data-ttu-id="cd61d-141">取得原始程式碼</span><span class="sxs-lookup"><span data-stu-id="cd61d-141">Get the source code</span></span>

<span data-ttu-id="cd61d-142">本教學課程的來源 [可在 GitHub 上](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/BlinkTutorial)取得 <span class="docon docon-navigate-external x-hidden-focus"></span> 。</span><span class="sxs-lookup"><span data-stu-id="cd61d-142">The source for this tutorial is [available on GitHub](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/BlinkTutorial) <span class="docon docon-navigate-external x-hidden-focus"></span>.</span></span>

## <a name="next-steps"></a><span data-ttu-id="cd61d-143">後續步驟</span><span class="sxs-lookup"><span data-stu-id="cd61d-143">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="cd61d-144">瞭解如何從感應器讀取環境條件</span><span class="sxs-lookup"><span data-stu-id="cd61d-144">Learn how to read environmental conditions from a sensor</span></span>](../tutorials/temp-sensor.md)
