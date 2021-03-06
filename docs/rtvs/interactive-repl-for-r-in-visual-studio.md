---
title: R 用の対話型 REPL
description: エディター ウィンドウと統合される Visual Studio の R 用対話型 REPL 環境を使う方法について説明します。
ms.date: 06/28/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 7109e74e858aa308b8f49e6e1e335478f801070b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62815005"
---
# <a name="work-with-the-r-interactive-window"></a>R 対話型ウィンドウの使用

R Tools for Visual Studio (RTVS) では R 対話型ウィンドウが提供されます。これは **REPL** (Read-Evaluate-Print-Loop) ウィンドウとも呼ばれ、R コードを入力してすぐに結果を確認できます。 対話型ウィンドウでは、IntelliSense だけでなく、すべてのモジュール、構文、および変数を使用できます。

また、対話型ウィンドウは通常の R エディター ウィンドウと統合されます。 コードを選択して **Ctrl**+**Enter** キーを押すか右クリックして **[対話形式で実行]** を選択できます。コードは、直接入力した場合と同じように、対話型ウィンドウで 1 行ずつ実行されます。 カーソルがエディター ウィンドウの単一行にある状態で **Ctrl**+**Enter** キーを押すと、その行は対話型ウィンドウに送信されてから、カーソルが次の行に移動します。 このように **Ctrl**+**Enter** キーを繰り返し押すだけで、コードをステップ スルーできます。

これらの機能を利用するには、「[R の概要](getting-started-with-r.md)」チュートリアルおよびこの記事のセクションの内容に従います。 [コード スニペット](code-snippets-for-r.md)は、R エディター ウィンドウの場合と同じように対話型ウィンドウでも機能します。

## <a name="overview-of-the-interactive-window"></a>対話型ウィンドウの概要

次のように、有効な R コードを入力し、行の最後で **Enter** キーを押すと、その行でコードが実行されます。

```repl
> 3 + 3
[1] 6
```

また、入力した単一行の任意の場所で **Enter** キーを押すと、その行が実行されます。

REPL での以前の入力と出力はすべて読み取り専用となり、変更できません。 ただし、ウィンドウからはいつでもテキストを選択してコピーおよび貼り付けることができます。 貼り付けられたコードは、1 行ずつ入力した場合と同じように実行されます。

つまり、ステートメントの入力を開始し、**Enter** キーを押すと、RTVS はステートメントを続行する必要があるタイミングを認識し、左の適切なインデントで + プロンプトを使用して複数行モードを入力します。 また、RTVS は次のようにかっこ、角かっこ、および中かっこも入力します。

![対話型ウィンドウの複数行のステートメント エントリ](media/repl-multiline-entry.png)

この複数行モードで **Enter** キーを押した場合にコード ブロックが実行されるのは、ブロックの末尾にある場合のみです。それ以外の場合は、改行が挿入されます。 ただし、任意の位置で **Ctrl**+**Enter** キーを押せば、そのコード ブロックをすぐに実行できます。

### <a name="toolbar-commands"></a>ツール バー コマンド

対話型ウィンドウとそのツールバーを以下に示します。

![対話型ウィンドウとツール バー](media/repl-window.png)

ツール バー コマンドは次のとおりです。そのほとんどに対応するキーボードがあり、**[R Tools]** の **[セッション]** か **[R Tools]** の **[作業ディレクトリ]** メニュー (または前述のとおり) でも使用可能です。

| ボタン | コマンド | キーの組み合わせ | 説明 |
| --- | --- | --- | --- |
| ![[リセット] ボタン](media/repl-toolbar-01-reset.png) | リセット | **Ctrl** + **Shift** + **F10** | すべての変数と履歴を消去し、対話型ウィンドウ セッションをリセットします。 |
| ![[クリア] ボタン](media/repl-toolbar-02-clear.png) | Clear | **Ctrl** + **L** | 対話型ウィンドウに表示されている出力を消去します。セッション変数や履歴には影響しません。 |
| ![[履歴] ボタン](media/repl-toolbar-03-history.png) | 過去の履歴コマンド<br/>次の履歴コマンド | **↑**、**↓**<br/>**Alt**+**↑**、**Alt**+**↓** | 複数行コード ブロックの特定の動作で、履歴をスクロールします。 「[履歴](#history)」を参照してください。 |
| ![[ワークスペースの読み込み] ボタン](media/repl-toolbar-04-load-workspace.png) | ワークスペースの読み込み | N/A | 以前に保存したワークスペースを読み込みます (「[ワークスペースとセッション](#workspaces-and-sessions)」を参照)。 |
| ![[作業状態の保存] ボタン](media/repl-toolbar-05-save-workspace-as.png)| 作業状態の保存 | N/A | セッションの現在の状態をワークスペースとして、保存します (「[ワークスペースとセッション](#workspaces-and-sessions)」を参照)。 |
| ![[R スクリプトのソース化] ボタン](media/repl-toolbar-06-source-r-script.png) | R スクリプトのソース化 | **Ctrl** + **Shift** + **S** | Visual Studio エディターで現在アクティブな R スクリプトを使用して `source` を呼び出します。これにより、コードが実行されます。  このボタンは、R ファイルが Visual Studio エディターで開いている場合にのみ表示されます。 |
| ![[エコーによる R スクリプトのソース化] ボタン](media/repl-toolbar-07-source-r-script-with-echo.png) | エコーによる R スクリプトのソース化 | **Ctrl**+**Shift**+**Enter** | [R スクリプトのソース化] と同じですが、対話型ウィンドウにはスクリプトのコンテンツが表示されます。 |
| ![[R の割り込み] ボタン](media/repl-toolbar-08-interrupt-r.png)| R の割り込み | **Esc** | このセクションの冒頭で示したスクリーンショットの `while` ループなど、対話型ウィンドウで実行中のコードを停止します。 |
| ![[デバッガーのアタッチ] ボタン](media/repl-toolbar-09b-attach-debugger.png)| デバッガーのアタッチ | N/A | **[デバッグ]** の **[R インタラクティブ型に接続]** コマンドを使用することもできます。 |
| ![[作業ディレクトリをソース ファイルの場所に設定] ボタン](media/repl-toolbar-10-set-working-directory-source.png)| 作業ディレクトリをソース ファイルの場所に設定 | **Ctrl**+**Shift**+**E** | 対話型ウィンドウに最後に読み込まれたソース ファイルに作業ディレクトリを設定します (`source` を使用)。 「[作業ディレクトリ](#working-directory)」を参照してください。 |
| ![[作業ディレクトリをプロジェクトの場所に設定] ボタン](media/repl-toolbar-11-set-working-directory-to-project.png) | 作業ディレクトリをプロジェクトの場所に設定 | **Ctrl** + **Shift** + **P** | Visual Studio に現在読み込まれているプロジェクトのルートに作業ディレクトリを設定します。 「[作業ディレクトリ](#working-directory)」を参照してください。 |
| (テキスト フィールド) | 作業ディレクトリの選択 | N/A | 作業ディレクトリの直接入力フィールド。 「[作業ディレクトリ](#working-directory)」を参照してください。 |

## <a name="workspaces-and-sessions"></a>ワークスペースとセッション

対話型ウィンドウでコードを実行すると、現在のセッションでコンテキストが作成されます。 コンテキストはグローバル変数、関数定義、ライブラリの読み込みなどで構成されます。 このコンテキストはまとめて*ワークスペース*と呼ばれます。ワークスペースはいつでも保存して読み込むことができます。

**[作業状態の保存]** ボタンを選択するか、**[R Tools]**、**[セッション]**、**[作業状態の保存]** コマンドの順に選択すると、場所とファイル名 (既定の拡張子は *.RData*) の入力が求められます。

特定のファイル名 (既定値は *.RData*) を使用してワークスペースを保存するには、REPL で **[作業状態の保存]** ボタンをクリックします。

以前に保存したワークスペースを再読み込みするには、**[ワークスペースの読み込み]** ボタンを選択するか **[R Tools]**、**[セッション]**、**[ワークスペースの読み込み]** の順に選択して、ワークスペース ファイルに移動します。

**[リセット]** ボタンをクリックするか、**[R Tools]**、**[セッション]**、**[リセット]** の順に選択すると、セッション コンテキストが消去されます。 リモート セッションを使用している場合、リセットによりリモート コンピューター上のユーザー プロファイルも削除され、そこに格納されているすべてのファイルが消去されます  (「[ワークスペース](r-workspaces-in-visual-studio.md#directories-on-local-and-remote-computers)」を参照)。

## <a name="working-directory"></a>作業ディレクトリ

開発者は通常、対話型セッション中に作業ディレクトリの変更が必要になります。 ツール バーの **[R Tools]** から選択できる **[作業ディレクトリ]** メニューとプロジェクト コンテキスト メニューで使用可能なさまざまなコマンドを使用することで、ソース ファイルの場所、プロジェクトの場所、またはその他の任意の場所に作業ディレクトリを簡単に設定できます。 そうすることで、ファイルの参照時に絶対パス名や長い相対パス名を入力せずに済みます。

## <a name="history"></a>履歴

対話型ウィンドウに入力するすべての行にはエディターから送信される行が含まれ、REPL の履歴に保持されます。 その後、おそらくコマンド ラインで慣れている上下方向キーを使用して履歴を移動することができます。

ただし、現在の行で入力を開始して、上方向キーを押した場合、その現在の行は、まだ実行していない場合でも履歴に保持される点が異なります。

対話型ウィンドウ内の履歴は、複数行にまたがる他のコード ブロックのステートメントでもインテリジェントに機能します。 上下方向キーで履歴を循環すると、複数行のコード ブロックが単位全体として取得され、現在のエントリとして表示されます。 この時点で、方向キーを使用して、先頭または最後に到達するまで 1 行ずつそのコード ブロックを移動します。 コード ブロックの先頭では、上方向キーを使用して履歴内の前の項目を取得します。最後の行では、下方向キーを使用して次の項目を取得します。

この動作は、上方向キーと **Enter** キーストロークを組み合わせて使用し、履歴の最後の項目を再実行する一般的なケースの場合です。当然ながら、上方向キーを押して複数行のコード ブロックに移動すると編集ができるようになります。

複数行のコード ブロックに移動しないようにする場合は、ツール バーのボタンを使用するか、**Alt**+**↑** キーおよび **Alt**-**↓** キーを使用します。この場合、すべてのブロックが単一行として扱われます。

履歴機能を理解する最も簡単な方法は、対話型ウィンドウで試してみることです。 次のコードには、いくつかの適切な単一行のステートメントと複数行のステートメントが示されています。 ただし、適切な履歴を作成するには、各ステートメントでコピー/貼り付けを使用します  (コードを別のコード ファイルに貼り付けてから、**Ctrl**+**Enter** キーを使用して対話型ウィンドウに行を送信することもできます)。

```R
3 + 3

4 + 4

5 + 5

add <- function (x, y) {
  return (x + y)
}

sub <- function (x, y) {
  return (x - y)
}
```