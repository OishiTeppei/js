問題：ハンバーガーメニューを作って、ハンバーガーメニューを押したときに、htmlに用意されているナビゲーションメニューが表示されるように実装してください(デザインは気にしなくてよいとする)

解答：

1 style.cssに下記を追加

/* ボタンのスタイル */
/* ハンバーガーボタンの基準 */
.burger {
    position: relative;
    width: 40px;
    height: 30px;
    cursor: pointer;
    display: none;
}

/* 3本線の共通スタイル */
.bar {
    display: block;
    position: absolute;
    /* 絶対配置 */
    left: 0;
    width: 100%;
    height: 3px;
    /* 線の太さ */
    background-color: #333;
    /* 線の色 */
    border-radius: 2px;

    /* アニメーションのための設定 */
    transition: transform 0.3s ease-in-out,
        opacity 0.3s ease-in-out,
        top 0.3s ease-in-out,
        bottom 0.3s ease-in-out;
}

/* 1本目の線（上） */
.bar:nth-child(1) {
    top: 0;
}

/* 2本目の線（真ん中） */
.bar:nth-child(2) {
    top: 50%;
    transform: translateY(-50%);
    /* 垂直方向中央揃え */
}

/* 3本目の線（下） */
.bar:nth-child(3) {
    bottom: 0;
}

/* .is-open クラスが付いた時のスタイル 
*/

/* 1. 真ん中の線を消す */
.burger.is-open .bar:nth-child(2) {
    opacity: 0;
}

/* 2. 上の線(1本目)を中央に移動させ、45度回転 */
.burger.is-open .bar:nth-child(1) {
    top: 50%;
    /* 中央の位置に移動 */
    transform: translateY(-50%) rotate(45deg);
    /* Y軸補正しつつ回転 */
}

/* 3. 下の線(3本目)を中央に移動させ、-45度回転 */
.burger.is-open .bar:nth-child(3) {
    bottom: 50%;
    /* 中央の位置に移動 */
    transform: translateY(50%) rotate(-45deg);
    /* Y軸補正しつつ回転 */
}


2 script.jsコードに追加

const burger = document.querySelector('.burger');
    const nav = document.querySelector('.nav-menu');
    burger.addEventListener('click', () => {
      burger.classList.toggle('is-open');
      nav.classList.toggle('is-open');
      console.log('クリックされました');
    });










