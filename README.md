<!-- ffxiv-tc-port 繁體中文說明開始 -->
# WrathCombo.API(台服 fork)

由 Ethan Henderson（zbee，Team Wrath）開發的函式庫，提供與 `WrathCombo` 插件 IPC 互動所需的
列舉、資料型別與強型別包裝方法，避免消費端自己複製特徵碼與追 IPC 變更紀錄。

## 台服 fork 的目的

跟隨艦隊釘 API13 / net9，`.csproj` 只改兩處，不動任何 IPC 介面內容：

- `TargetFramework` 從 `net10.0-windows` 改回 `net9.0-windows7.0`（艦隊釘 API13 / net9）。
- `GeneratePackageOnBuild` 改為 `false`（我們不發 NuGet 套件，消費端一律走子模組 +
  `ProjectReference`）。`LangVersion` 維持 14，因上游碼用了 C# 14 的 extension 區塊與
  `field` 關鍵字，需要 .NET 10 SDK 編譯；目標框架仍是 net9，不影響執行期。

## 與上游的差異

上述 csproj 兩處調整。另外目前 pin 落後上游：`ComboTargetTypeKeys` 列舉值上游已改名
（`SingleTargetDPS`→`SingleTarget`、`AoEDPS`→`MultiTarget` 等），我們尚未同步，屬版本落差
非刻意改動。

## 誰在用它

艦隊裡目前只有 **`AutoDuty`** 一個插件消費。

---

以下為上游原始 README，內容未經修改：

<!-- ffxiv-tc-port 繁體中文說明結束 -->

# WrathCombo.API

WrathCombo.API provides the enum and similar data
used by [Wrath Combo's](https://github.com/PunishXIV/WrathCombo) IPC (read: API), the
IPC Methods themselves, and wrappers for those IPC
Methods that are typed more strongly than what
Dalamud IPC allows for.\
All in the sake of not having to copy over
signatures, data, or keep up with the IPC changelog
yourself.

You can find the full documentation for the IPC
itself [here](https://github.com/PunishXIV/WrathCombo/blob/main/docs/IPC.md).

## Support

It's best to open issues here; but opening issue posts in the
[puni.sh discord server](https://discord.gg/Zzrcc8kmvy)'s
[Wrath Issues Forum](https://discord.com/channels/1001823907193552978/1271175826246865026)
(with `[API]` in the title) is also fine.

## Changes

See
[Docs/Changes.md](https://github.com/PunishXIV/WrathCombo.API/blob/main/Docs/Changes.md)
for the changelog.

> [!TIP]
> You can keep up to date with the latest changes to the IPC by subscribing to the
> GitHub Atom feeds for the core Wrath Combo IPC documentation, and the changes
> file here. For example, you can do this very easily with
> [Blogtrottr](https://blogtrottr.com/).\
> This package's changes feed:
> ```
> https://github.com/PunishXIV/WrathCombo.API/commits/main/Docs/Changes.md.atom
> ```
>
>
> ---
>
>
> Wrath Combo IPC Documentation feed:
> ```
> https://github.com/PunishXIV/WrathCombo/commits/main/docs/IPC.md.atom
> ```
> or @zbee's branch for upcoming changes: (though this link is more likely to move)
> ```
> https://github.com/zbee/WrathCombo/commits/IPC/docs/IPC.md.atom
> ```

---

    WrathCombo.API: Everything you need to work with Wrath Combo's IPC.
    Copyright (C) 2025  Ethan Henderson (zbee) <ethan@zbee.codes>

     This program is free software: you can redistribute it and/or modify
     it under the terms of the GNU Affero General Public License as published
     by the Free Software Foundation, either version 3 of the License, or
     (at your option) any later version.

     This program is distributed in the hope that it will be useful,
     but WITHOUT ANY WARRANTY; without even the implied warranty of
     MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
     GNU Affero General Public License for more details.

     You should have received a copy of the GNU Affero General Public License
     along with this program. If not, see <https://www.gnu.org/licenses/>. 

