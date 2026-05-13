# 課題管理アプリの処理フロー

以下はプログラムの動作の流れです。

```mermaid
flowchart TD
    Start([プログラム開始]) --> Init[tasks.csv の存在確認]
    Init --> Menu([メインメニューの表示])
    
    Menu --> InputChoice{メニュー番号を選択}
    
    InputChoice -->|1| AddTask[データの追加]
    AddTask --> A1[入力チェック]
    A1 --> A2[tasks.csv に追記]
    A2 --> WaitEnter

    InputChoice -->|2| Extract[リマインダーの抽出]
    Extract --> E1[未提出・7日以内を抽出]
    E1 --> E2[reminders.csv 保存 & 表示]
    E2 --> WaitEnter

    InputChoice -->|3| Delete[データの削除]
    D1[一覧表示] --> D2[番号選択]
    Delete --> D1
    D2 --> D3[csvを上書き保存]
    D3 --> WaitEnter

    InputChoice -->|4| Exit([アプリを終了])
    
    WaitEnter([Enterキー入力待ち]) --> Menu
