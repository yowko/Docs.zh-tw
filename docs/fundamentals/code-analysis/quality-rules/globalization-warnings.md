---
title: " (程式碼分析) 的全球化規則"
description: 瞭解程式碼分析規則的全球化規則
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.globalizationrules
helpviewer_keywords:
- rules, globalization
- globalization rules
- globalization [Visual Studio], rules
- managed code analysis rules, globalization rules
author: gewarren
ms.author: gewarren
ms.openlocfilehash: 83ecc52c5e20e074c6c1aed68204a574494f42d5
ms.sourcegitcommit: 2e4adc490c1d2a705a0592b295d606b10b9f51f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2020
ms.locfileid: "96586148"
---
# <a name="globalization-rules"></a>全球化規則

全球化規則支援可供世界用的程式庫和應用程式。

## <a name="in-this-section"></a>本節內容

|規則|描述|
|----------|-----------------|
|[CA1303:不要將常值當作已當地語系化的參數傳遞](ca1303.md)|外部可見的方法會將字串常值做為參數傳遞至 .NET 的函式或方法，且該字串應可當地語系化。|
|[CA1304:必須指定 CultureInfo](ca1304.md)|方法或建構函式會呼叫具有接受 System.Globalization.CultureInfo 參數之多載的成員，且方法或建構函式未呼叫採用 CultureInfo 參數的多載。 未提供 CultureInfo 或 System.IFormatProvider 物件時，多載成員所提供的預設值可能不會有您希望在所有地區設定中都有的效果。|
|[CA1305:必須指定 IFormatProvider](ca1305.md)|方法或建構函式所呼叫的一個或多個成員具有可接受 System.IFormatProvider 參數的多載，但該方法或建構函式並未呼叫可接受 IFormatProvider 參數的多載。 未提供 System.Globalization.CultureInfo 或 IFormatProvider 物件時，多載成員所提供的預設值可能不會有您希望在所有地區設定中都有的效果。|
|[CA1307:指定 StringComparison 以提升明確性](ca1307.md)|字串比較作業會使用未設定 StringComparison 參數的方法多載。|
|[CA1308:必須將字串標準化為大寫字母](ca1308.md)|字串應該標準化為大寫字母。 當一小組的字元轉換成小寫字母時，它們無法構成來回行程。|
|[CA1309:使用循序的 StringComparison](ca1309.md)|非語言的字串比較作業未將 StringComparison 參數設定為 Ordinal 或 OrdinalIgnoreCase。 藉由明確地將參數設定為 StringComparison.Ordinal 或 StringComparison.OrdinalIgnoreCase，您的程式碼通常可以提升速度、更為正確，也更加可靠。|
|[CA1310：指定 StringComparison 以提升正確性](ca1310.md)|字串比較作業會使用未設定 StringComparison 參數的方法多載，並預設使用特定文化特性的字串比較。|
|[CA2101 必須：指定 P/Invoke 字串引數的封送處理](ca2101.md)|平台叫用成員允許部分信任的呼叫端、具有字串參數，且不會明確地封送處理字串。 這樣會造成安全性弱點。|
