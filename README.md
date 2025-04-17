# MATLAB をコンパイルするデモコード

## 意図

MATLAB コードをスパコン上で多数並列実行する際、MATLAB の起動時間がボトルネックとなる問題を解消することを目的としています。

### 背景

- MATLAB の起動には約 30 秒かかるため、短時間で終了するコードを多数実行する場合、起動時間が全体の処理時間を大幅に増加させる可能性があります。

#### 例

- 10 秒で終了するコードを 10,000 回実行する場合を考えます。
- 各コードは 1 コアのみを使用すると仮定します。
- 100 並列で実行した場合:
    - 計算時間: 10 秒 × 10,000 回 ÷ 100 並列 = 1,000 秒
    - 起動時間を含む場合: (10 秒 + 30 秒) × 10,000 回 ÷ 100 並列 = 4,000 秒
    - 起動時間が原因で 4 倍遅くなります。

### 解決策

MATLAB コードをコンパイルし、`matlab -nodesktop -r "magicsquare 4"` の代わりに、`./magicsquare 4` のように実行できる形式にすることで、起動時間を削減し、全体の処理時間を短縮します。

## 参考文献

このリポジトリは MATLAB のコンパイルを試すためのものです。以下のリンクを参考にしています:  
[MATLAB Compiler ドキュメント](https://jp.mathworks.com/help/compiler/create-standalone-app-from-matlab-function.html)

## コンパイル方法

以下のコマンドを MATLAB 内で実行してください:

```matlab
appFile = "magicsquare.m";
buildResults = compiler.build.standaloneApplication(appFile);
```

## 実行方法

各 OS に応じて以下のコマンドを使用してください:

- **Windows**  
    ```cmd
    !magicsquare 4
    ```

- **Linux**  
    ```bash
    !./magicsquare 4
    ```

- **macOS**  
    ```matlab
    system(['./run_magicsquare.sh ', matlabroot, ' 4']);
    ```