---
title: 快速入門-使用 .NET 驅動 Raspberry Pi 感知 HAT
description: 使用 Raspberry Pi 的附加元件，在5分鐘內開始使用 .NET IoT 程式庫。
author: camsoper
ms.author: casoper
ms.date: 11/13/2020
ms.topic: quickstart
ms.prod: dotnet
ms.openlocfilehash: 2919db55304590f5557aa0cbda50cc4bd6640443
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2020
ms.locfileid: "96739526"
---
# <a name="quickstart---use-net-to-drive-a-raspberry-pi-sense-hat"></a>快速入門-使用 .NET 驅動 Raspberry Pi 感知 HAT

Raspberry Pi [感知 HAT](https://www.raspberrypi.org/products/sense-hat/) <span class="docon docon-navigate-external x-hidden-focus"></span> (**H** 硬體 ttached **** on **T** op) 是 Raspberry Pi 的附加元件面板。 意義 HAT 配備了8× 8 RGB LED 矩陣、五個按鈕的搖桿，並且包含下列感應器：

- 迴轉儀
- 加速計
- 磁力計
- 溫度
- 氣壓
- 溼度

本快速入門會使用 .NET 來取出 HAT HAT 的感應器值、回應搖桿輸入，以及驅動 LED 矩陣。

## <a name="prerequisites"></a>先決條件

- [!INCLUDE [prereq-rpi](../includes/prereq-rpi.md)]
- 意義 HAT

[!INCLUDE [prepare-pi-i2c](../includes/prepare-pi-i2c.md)]

## <a name="run-the-quickstart"></a>執行快速入門

將意義 HAT 附加至您的 Raspberry Pi。 從 Raspberry Pi (本機或遠端) 上的 Bash 提示字元中，執行下列命令：

```bash
. <(wget -q -O - https://aka.ms/dotnet-iot-sensehat-quickstart)
```

此命令會下載並執行腳本。 指令碼：

- 安裝 .NET SDK。
- 複製包含 HAT HAT 快速入門專案的 GitHub 存放庫。
- 建置專案。
- 執行專案。

在顯示感應器資料時觀察主控台輸出。 LED 矩陣會在藍色的欄位上顯示黃色圖元。 以任何方向按住操縱杆會移動該方向的黃色圖元。 按一下中央搖桿按鈕會導致背景從藍色切換為紅色。

## <a name="get-the-source-code"></a>取得原始程式碼

本快速入門的來源 [可在 GitHub 上](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/quickstarts/SenseHat.Quickstart)取得 <span class="docon docon-navigate-external x-hidden-focus"></span> 。

## <a name="next-steps"></a>後續步驟

> [!div class="nextstepaction"]
> [瞭解如何使用一般用途的輸入/輸出來閃爍 LED](../tutorials/blink-led.md)
