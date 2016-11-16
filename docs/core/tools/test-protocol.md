---
title: ".NET Core CLI 測試通訊協定"
description: ".NET Core CLI 測試通訊協定"
keywords: .NET, .NET Core
author: mairaw
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 88cba792-3640-41de-b55d-00f575e9d5e2
translationtype: Human Translation
ms.sourcegitcommit: 81e7604f0a646e5de9c2ed35ff3b6ef6d7fb2e71
ms.openlocfilehash: a35385cbb08614493fdcfc74504b00178dc532ea

---

#<a name="net-core-cli-test-communication-protocol"></a>.NET Core CLI 測試通訊協定

## <a name="introduction"></a>簡介
只要將連接埠傳遞至 dotnet test，就會在設計階段執行命令。 這表示 dotnet test 會連接到這個使用 TCP 的連接埠，然後與連接到該連接埠的任何其他項目交換已建立的一組訊息。 發生這種情況時，執行器也會收到 dotnet test 用來與之通訊的新連接埠。 執行器也使用 TCP 與 dotnet test 通訊的原因是在設計模式中，不足以將結果輸出到主控台。 這個命令需要傳送包含測試執行結果的配接器結構訊息。

### <a name="communication-protocol-at-design-time"></a>設計階段的通訊協定。

1. 在設計階段期間，因為 dotnet test 會在啟動時連接到連接埠，所以配接器需要接聽該連接埠，否則 dotnet test 將會失敗。 我們會這麼做，以在 dotnet test 執行並嘗試取得配接器的連接埠之前進行繫結和接聽，讓配接器可以保留所需的所有連接埠。
2. dotnet test 在啟動之後，會將 TestSession.Connected 訊息傳送給配接器，指出已準備好接收訊息。
3. 可以傳送內含通訊協定之配接器版本的選擇性[版本檢查](https://github.com/dotnet/cli/blob/rel/1.0.0/src/Microsoft.Extensions.Testing.Abstractions/Messages/ProtocolVersionMessage.cs)訊息。 Dotnet test 將會送回所支援通訊協定的版本。

所有訊息的格式說明如下︰[Message.cs](https://github.com/dotnet/cli/blob/rel/1.0.0/src/Microsoft.Extensions.Testing.Abstractions/Messages/Message.cs)。 每個訊息的承載格式都是以類別的連結描述，而類別用來序列化/還原序列化通訊協定描述中的資訊。

#### <a name="test-execution"></a>測試執行
![測試執行](./media/test-protocol/dotnet-test-execute.png)

1. 執行選擇性版本檢查之後，配接器會傳送 TestExecution.GetTestRunnerProcessStartInfo 以及想要在其內執行的 [tests](https://github.com/dotnet/cli/blob/rel/1.0.0/src/Microsoft.Extensions.Testing.Abstractions/Messages/RunTestsMessage.cs)。 Dotnet test 會在配接器可用來啟動執行器的 [TestStartInfo](https://github.com/dotnet/cli/blob/rel/1.0.0/src/Microsoft.DotNet.Tools.Test/TestStartInfo.cs) 承載內傳回 FileName 和引數。 過去，我們會傳送測試清單當成該引數的一部分來執行，但會實際徹底檢查一些測試專案的命令列大小限制。
  1. 我們會傳送執行器應該連接的連接埠，當成引數的一部分，以及，針對執行測試，--wait-command 旗標指出執行器應該連接至連接埠，並等待命令，而不是繼續進行並執行測試。
2. 配接器目前可以啟動執行器，並附加到它以進行偵錯 (如果選擇這麼做)。
3. 執行器在啟動之後，會將 TestRunner.WaitCommand 訊息傳送給 dotnet test，指出已準備好接收命令，而 dotnet test 在此時會使用要執行的[測試](https://github.com/dotnet/cli/blob/rel/1.0.0/src/Microsoft.Extensions.Testing.Abstractions/Messages/RunTestsMessage.cs)清單來傳送 TestRunner.Execute。 這會略過上面所述的命令列大小限制。
4. 執行器接著會針對每個測試將 TestExecution.TestStarted 傳送給 dotnet test (並往前轉遞給配接器)，原因是它們使用其內的[測試](https://github.com/dotnet/cli/blob/rel/1.0.0/src/Microsoft.Extensions.Testing.Abstractions/Test.cs)資訊開始。
5. 執行器也會針對每個測試將 TestExecution.TestResult 與測試的[個別結果](https://github.com/dotnet/cli/blob/rel/1.0.0/src/Microsoft.Extensions.Testing.Abstractions/TestResult.cs)傳送給 dotnet test (並將它轉遞給配接器)。
6. 所有測試都完成之後，執行器會將 TestRunner.Completed 訊息傳送給 dotnet test，而 dotnet test 會以 TestExecution.Completed 形式傳送給配接器。
7. 完成配接器之後，會將 TestSession.Terminate 傳送給 dotnet test，以關閉 dotnet test。

#### <a name="test-discovery"></a>測試探索
![測試探索](./media/test-protocol/dotnet-test-discover.png)

1. 執行選擇性版本檢查之後，配接器會傳送 TestDiscovery.Start 訊息。 在此情況下，因為配接器不需要附加至處理序，所以 dotnet test 會自行啟動執行器。 同時，因為沒有要傳遞給執行器的長引數清單，所以需要將 no --wait-command 旗標傳遞給執行器。 dotnet test 只會將 --list 引數傳遞給執行器，這表示執行器不應該執行測試，只是列出它們。
2. 執行器接著會針對每個找到的[測試](https://github.com/dotnet/cli/blob/rel/1.0.0/src/Microsoft.Extensions.Testing.Abstractions/Test.cs)將 TestDiscovery.TestFound 傳送給 dotnet test (並往前轉遞給配接器)。
3. 找到所有測試之後，執行器會將 TestRunner.Completed 訊息傳送給 dotnet test，而 dotnet test 會以 TestDiscovery.Completed 形式傳送給配接器。
4. 完成配接器之後，會將 TestSession.Terminate 傳送給 dotnet test，以關閉 dotnet test。


<!--HONumber=Nov16_HO1-->


