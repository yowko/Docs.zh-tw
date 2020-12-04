---
title: 快速入門-使用 .NET 驅動 Raspberry Pi 感知 HAT
description: 使用 Raspberry Pi 的附加元件，在5分鐘內開始使用 .NET IoT 程式庫。
author: camsoper
ms.author: casoper
ms.date: 11/13/2020
ms.topic: quickstart
ms.prod: dotnet
ms.openlocfilehash: 09e0c46a08e08a2021a9dffe214d3d62d6fb8ec5
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2020
ms.locfileid: "96586629"
---
# <a name="quickstart---use-net-to-drive-a-raspberry-pi-sense-hat"></a><span data-ttu-id="7c873-103">快速入門-使用 .NET 驅動 Raspberry Pi 感知 HAT</span><span class="sxs-lookup"><span data-stu-id="7c873-103">Quickstart - Use .NET to drive a Raspberry Pi Sense HAT</span></span>

<span data-ttu-id="7c873-104">Raspberry Pi [意義 HAT](https://www.raspberrypi.org/products/sense-hat/) <span class="docon docon-navigate-external x-hidden-focus"></span> 是 Raspberry Pi 的附加元件。</span><span class="sxs-lookup"><span data-stu-id="7c873-104">The Raspberry Pi [Sense HAT](https://www.raspberrypi.org/products/sense-hat/) <span class="docon docon-navigate-external x-hidden-focus"></span> is an add-on board for Raspberry Pi.</span></span> <span data-ttu-id="7c873-105">意義 HAT 配備了8× 8 RGB LED 矩陣、五個按鈕的搖桿，並且包含下列感應器：</span><span class="sxs-lookup"><span data-stu-id="7c873-105">The Sense HAT is equipped with an 8×8 RGB LED matrix, a five-button joystick, and includes the following sensors:</span></span>

- <span data-ttu-id="7c873-106">迴轉儀</span><span class="sxs-lookup"><span data-stu-id="7c873-106">Gyroscope</span></span>
- <span data-ttu-id="7c873-107">加速計</span><span class="sxs-lookup"><span data-stu-id="7c873-107">Accelerometer</span></span>
- <span data-ttu-id="7c873-108">磁力計</span><span class="sxs-lookup"><span data-stu-id="7c873-108">Magnetometer</span></span>
- <span data-ttu-id="7c873-109">溫度</span><span class="sxs-lookup"><span data-stu-id="7c873-109">Temperature</span></span>
- <span data-ttu-id="7c873-110">氣壓</span><span class="sxs-lookup"><span data-stu-id="7c873-110">Barometric pressure</span></span>
- <span data-ttu-id="7c873-111">溼度</span><span class="sxs-lookup"><span data-stu-id="7c873-111">Humidity</span></span>

<span data-ttu-id="7c873-112">本快速入門會使用 .NET 來取出 HAT HAT 的感應器值、回應搖桿輸入，以及驅動 LED 矩陣。</span><span class="sxs-lookup"><span data-stu-id="7c873-112">This quickstart uses .NET to retrieve sensor values from the Sense HAT, respond to joystick input, and drive the LED matrix.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7c873-113">先決條件</span><span class="sxs-lookup"><span data-stu-id="7c873-113">Prerequisites</span></span>

- [!INCLUDE [prereq-rpi](../includes/prereq-rpi.md)]
- <span data-ttu-id="7c873-114">意義 HAT</span><span class="sxs-lookup"><span data-stu-id="7c873-114">Sense HAT</span></span>

[!INCLUDE [prepare-pi-i2c](../includes/prepare-pi-i2c.md)]

## <a name="run-the-quickstart"></a><span data-ttu-id="7c873-115">執行快速入門</span><span class="sxs-lookup"><span data-stu-id="7c873-115">Run the quickstart</span></span>

<span data-ttu-id="7c873-116">將意義 HAT 附加至您的 Raspberry Pi。</span><span class="sxs-lookup"><span data-stu-id="7c873-116">Attach the Sense HAT to your Raspberry Pi.</span></span> <span data-ttu-id="7c873-117">從 Raspberry Pi (本機或遠端) 上的 Bash 提示字元中，執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="7c873-117">From a Bash prompt on the Raspberry Pi (local or remote), run the following command:</span></span>

```bash
. <(wget -q -O - https://aka.ms/dotnet-iot-sensehat-quickstart)
```

<span data-ttu-id="7c873-118">此命令會下載並執行腳本。</span><span class="sxs-lookup"><span data-stu-id="7c873-118">The command downloads and runs a script.</span></span> <span data-ttu-id="7c873-119">指令碼：</span><span class="sxs-lookup"><span data-stu-id="7c873-119">The script:</span></span>

- <span data-ttu-id="7c873-120">安裝 .NET SDK。</span><span class="sxs-lookup"><span data-stu-id="7c873-120">Installs the .NET SDK.</span></span>
- <span data-ttu-id="7c873-121">複製包含 HAT HAT 快速入門專案的 GitHub 存放庫。</span><span class="sxs-lookup"><span data-stu-id="7c873-121">Clones a GitHub repository that includes the Sense HAT quickstart project.</span></span>
- <span data-ttu-id="7c873-122">建置專案。</span><span class="sxs-lookup"><span data-stu-id="7c873-122">Builds the project.</span></span>
- <span data-ttu-id="7c873-123">執行專案。</span><span class="sxs-lookup"><span data-stu-id="7c873-123">Runs the project.</span></span>

<span data-ttu-id="7c873-124">在顯示感應器資料時觀察主控台輸出。</span><span class="sxs-lookup"><span data-stu-id="7c873-124">Observe the console output as sensor data is displayed.</span></span> <span data-ttu-id="7c873-125">LED 矩陣會在藍色的欄位上顯示黃色圖元。</span><span class="sxs-lookup"><span data-stu-id="7c873-125">The LED matrix displays a yellow pixel on a field of blue.</span></span> <span data-ttu-id="7c873-126">以任何方向按住操縱杆會移動該方向的黃色圖元。</span><span class="sxs-lookup"><span data-stu-id="7c873-126">Holding the joystick in any direction moves the yellow pixel in that direction.</span></span> <span data-ttu-id="7c873-127">按一下中央搖桿按鈕會導致背景從藍色切換為紅色。</span><span class="sxs-lookup"><span data-stu-id="7c873-127">Clicking the center joystick button causes the background to switch from blue to red.</span></span>

## <a name="get-the-source-code"></a><span data-ttu-id="7c873-128">取得原始程式碼</span><span class="sxs-lookup"><span data-stu-id="7c873-128">Get the source code</span></span>

<span data-ttu-id="7c873-129">本快速入門的來源 [可在 GitHub 上](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/quickstarts/SenseHat.Quickstart)取得。</span><span class="sxs-lookup"><span data-stu-id="7c873-129">The source for this quickstart is [available on GitHub](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/quickstarts/SenseHat.Quickstart).</span></span> <span class="docon docon-navigate-external x-hidden-focus"></span>

## <a name="next-steps"></a><span data-ttu-id="7c873-130">後續步驟</span><span class="sxs-lookup"><span data-stu-id="7c873-130">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7c873-131">瞭解如何使用一般用途的輸入/輸出來閃爍 LED</span><span class="sxs-lookup"><span data-stu-id="7c873-131">Learn to use General Purpose Input/Output to blink an LED</span></span>](../tutorials/blink-led.md)
