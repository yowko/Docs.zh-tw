### <a name="il-ret-not-allowed-in-a-try-region"></a>try 區域中不允許 IL ret

|   |   |
|---|---|
|詳細資料|不同於 JIT64 Just-In-Time 編譯器，RyuJIT (用於 .NET 4.6) 不允許在 try 區域中使用 IL ret 指令。 ECMA-335 規格不允許從 try 區域傳回，而且不會有已知的受控編譯器產生這類 IL。 不過，如果這類 IL 是由反映發出所產生，則 JIT64 編譯器將會執行這類 IL。|
|建議|如果應用程式產生在 try 區域中包含 ret opcode 的 IL，應用程式可以 .NET 4.5 為目標，即可使用舊的 JIT，以避免這項中斷。 或者，可以將產生的 IL 更新為在 try 區域之後傳回。|
|範圍|Edge|
|版本|4.6|
|類型|正在重定目標|

