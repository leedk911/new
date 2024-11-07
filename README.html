<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>2D 홍진혁 도망가기 게임</title>
    <style>
        body { margin: 0; overflow: hidden; }
        canvas { background: #87CEEB; display: block; }
        #info { position: absolute; top: 10px; left: 10px; color: black; }
        #balloon { position: absolute; background: white; border: 1px solid black; padding: 5px; display: none; }
    </style>
</head>
<body>
    <div id="info">
        <div>점수: <span id="score">0</span></div>
        <div>남은 시간: <span id="time">60</span></div>
    </div>
    <div id="balloon"></div>
    <canvas id="gameCanvas"></canvas>
    <script>
        const canvas = document.getElementById("gameCanvas");
        const ctx = canvas.getContext("2d");
        canvas.width = window.innerWidth; // 화면 너비
        canvas.height = window.innerHeight; // 화면 높이

        const playerImage = new Image();
        playerImage.src = 'player.png'; // 플레이어 이미지 경로

        const chaserImage = new Image();
        chaserImage.src = 'chaser.png'; // 김태이 이미지 경로

        const bananaImage = new Image();
        bananaImage.src = 'banana.png'; // 바나나 이미지 경로

        const obstacleImage = new Image();
        obstacleImage.src = '3208702.png'; // 일반 장애물 이미지 경로

        let player = { x: canvas.width / 2 - 25, y: canvas.height - 100, width: 50, height: 50, jump: false, velocityY: 0 };
        let chaser = { x: 0, y: canvas.height - 100, width: 50, height: 50, jump: false, velocityY: 0 }; // 왼쪽 끝에서 시작
        let obstacles = [];
        let score = 0;
        let timeLeft = 60;
        let gameOver = false;

        const playerSpeed = 12; // 홍진혁 속도 증가
        const playerJumpPower = -30; // 홍진혁 점프력 증가
        const chaserSpeed = 5; // 김태이 속도
        const chaserJumpPower = -15; // 김태이 점프력을 낮춤
        const obstacleSpeed = 7; // 장애물 속도
        const blockHeight = 30; // 각 칸의 높이

        let isChaserMovingRight = false;
        let isChaserMovingLeft = false;
        let isPlayerMovingRight = false;
        let isPlayerMovingLeft = false;

        let isSlowed = false; // 느려진 상태
        let showBalloon = false; // 말풍선 표시 여부
        let invincible = false; // 무적 상태

        const taunts = [
            "그것도 못 피하냐?", 
            "느리네!", 
            "어이, 좀 더 빠르게!", 
            "헐, 진짜 못하네!", 
            "실망이다!",
            "이걸 피하지 못해?"
        ]; // 랜덤 조롱 대사 배열

        document.addEventListener('keydown', onKeyDown);
        document.addEventListener('keyup', onKeyUp);
        setInterval(createObstacle, 2000);
        setInterval(updateTimer, 1000);
        requestAnimationFrame(gameLoop);

        function onKeyDown(event) {
            if (event.code === 'ArrowUp' && !player.jump) {
                player.jump = true;
                player.velocityY = playerJumpPower; // 플레이어 점프 시작
            }
            if (event.code === 'ArrowRight') {
                isPlayerMovingRight = true; // 오른쪽 이동 상태
            }
            if (event.code === 'ArrowLeft') {
                isPlayerMovingLeft = true; // 왼쪽 이동 상태
            }
            if (event.code === 'KeyD') {
                isChaserMovingRight = true; // 오른쪽 이동 상태
            }
            if (event.code === 'KeyA') {
                isChaserMovingLeft = true; // 왼쪽 이동 상태
            }
            if (event.code === 'KeyW' && !chaser.jump) {
                chaser.jump = true; // 김태이 점프 시작
                chaser.velocityY = chaserJumpPower; // 점프 속도 (낮춤)
            }
        }

        function onKeyUp(event) {
            if (event.code === 'ArrowRight') {
                isPlayerMovingRight = false; // 오른쪽 이동 상태 해제
            }
            if (event.code === 'ArrowLeft') {
                isPlayerMovingLeft = false; // 왼쪽 이동 상태 해제
            }
            if (event.code === 'KeyD') {
                isChaserMovingRight = false; // 오른쪽 이동 상태 해제
            }
            if (event.code === 'KeyA') {
                isChaserMovingLeft = false; // 왼쪽 이동 상태 해제
            }
        }

        function createObstacle() {
            const width = Math.random() * 100 + 30; // 너비: 30~130
            const height = Math.floor(Math.random() * 4 + 2) * blockHeight; // 높이: 60~150 (2~5칸)
            const isBanana = Math.random() < 0.3; // 30% 확률로 바나나 장애물 생성
            const obstacle = { 
                x: canvas.width + width, 
                y: canvas.height - (isBanana ? (Math.floor(Math.random() * 4 + 2) * blockHeight) : height), // 바나나 높이: 2~5칸
                width: width, 
                height: isBanana ? (Math.floor(Math.random() * 4 + 2) * blockHeight) : height, 
                type: isBanana ? 'banana' : 'regular' // 장애물 타입 추가
            };
            obstacles.push(obstacle);
        }

        function updateTimer() {
            timeLeft--;
            document.getElementById('time').innerText = timeLeft;
            if (timeLeft <= 0) {
                alert('시간이 끝났습니다! 최종 점수: ' + score);
                gameOver = true;
            }
        }

        function gameLoop() {
            if (gameOver) {
                ctx.drawImage(playerImage, 0, 0, canvas.width, canvas.height); // 전체 화면으로 이미지 그리기
                return;
            }

            ctx.clearRect(0, 0, canvas.width, canvas.height);

            // 배경 이동 효과
            ctx.fillStyle = '#87CEEB'; // 하늘색 배경
            ctx.fillRect(0, 0, canvas.width, canvas.height);

            // 장애물 처리
            obstacles.forEach((obstacle, index) => {
                obstacle.x -= obstacleSpeed; // 장애물 이동
                if (obstacle.type === 'banana') {
                    ctx.drawImage(bananaImage, obstacle.x, obstacle.y, obstacle.width, obstacle.height); // 바나나 이미지 그리기
                } else {
                    ctx.drawImage(obstacleImage, obstacle.x, obstacle.y, obstacle.width, obstacle.height); // 일반 장애물 이미지 그리기
                }

                // 장애물이 화면 밖으로 나가면 점수 추가
                if (obstacle.x < -obstacle.width) {
                    obstacles.splice(index, 1);
                    score += 10; // 점수 추가
                    document.getElementById('score').innerText = score; // 점수 표시
                }

                // 김태이 충돌 검사 및 슬로우 효과
                if (!chaser.jump && chaser.x < obstacle.x + obstacle.width &&
                    chaser.x + chaser.width > obstacle.x &&
                    chaser.y < obstacle.y + obstacle.height &&
                    chaser.y + chaser.height > obstacle.y) {
                    if (obstacle.type === 'banana' && !isSlowed) {
                        isSlowed = true; // 슬로우 상태 활성화
                        chaser.x -= 2 * 50; // 2칸 뒤로 미끄러짐
                        setTimeout(() => {
                            isSlowed = false; // 슬로우 해제
                        }, 1000); // 1초 후에 슬로우 해제
                        showBalloon = true; // 말풍선 표시
                    }
                }

                // 플레이어와 김태이 충돌 검사
                if (!player.jump && player.x < obstacle.x + obstacle.width &&
                    player.x + player.width > obstacle.x &&
                    player.y < obstacle.y + obstacle.height &&
                    player.y + player.height > obstacle.y) {
                    if (obstacle.type === 'banana') {
                        // 홍진혁이 바나나에 닿으면 김태이 쪽으로 이동
                        player.x -= 0.5 * 50; // 홍진혁이 0.5칸 뒤로 이동
                        showBalloon = true; // 말풍선 표시
                    } else {
                        // 홍진혁이 일반 장애물에 닿으면 게임 오버
                        alert('게임 오버! 최종 점수: ' + score);
                        gameOver = true;
                    }
                }

                // 플레이어와 김태이 충돌 검사
                if (chaser.x < player.x + player.width &&
                    chaser.x + chaser.width > player.x &&
                    chaser.y < player.y + player.height &&
                    chaser.y + chaser.height > player.y) {
                    alert('김태이가 잡았습니다! 최종 점수: ' + score);
                    gameOver = true;
                }
            });

            // 플레이어 점프 처리
            if (player.jump) {
                player.y += player.velocityY; // 점프 높이 적용
                player.velocityY += 1; // 중력 효과

                // 점프가 끝났는지 확인
                if (player.y >= canvas.height - 100) {
                    player.y = canvas.height - 100; // 착지
                    player.jump = false; // 점프 종료
                    player.velocityY = 0; // 속도 초기화
                }
            }

            // 김태이 점프 처리
            if (chaser.jump) {
                chaser.y += chaser.velocityY; // 점프 높이 적용
                chaser.velocityY += 1; // 중력 효과

                // 점프가 끝났는지 확인
                if (chaser.y >= canvas.height - 100) {
                    chaser.y = canvas.height - 100; // 착지
                    chaser.jump = false; // 점프 종료
                    chaser.velocityY = 0; // 속도 초기화
                }
            }

            // 플레이어 이동 처리
            if (isPlayerMovingRight) {
                player.x += playerSpeed; // 오른쪽 이동
            }
            if (isPlayerMovingLeft) {
                player.x -= playerSpeed; // 왼쪽 이동
            }

            // 김태이 이동 처리
            if (isChaserMovingRight) {
                chaser.x += chaserSpeed; // 오른쪽 이동
            }
            if (isChaserMovingLeft) {
                chaser.x -= chaserSpeed; // 왼쪽 이동
            }

            // 플레이어 그리기 (홍진혁)
            ctx.drawImage(playerImage, player.x, player.y, player.width, player.height); // 이미지로 그리기

            // 추격자 그리기 (김태이)
            ctx.drawImage(chaserImage, chaser.x, chaser.y, chaser.width, chaser.height); // 김태이 그리기

            // 말풍선 표시
            if (showBalloon) {
                const balloon = document.getElementById('balloon');
                balloon.style.display = 'block';
                balloon.style.left = (player.x + 10) + 'px'; // 홍진혁의 위치에 따라 말풍선 위치 조정
                balloon.style.top = (player.y - 30) + 'px'; // 말풍선 높이 조정
                balloon.innerText = taunts[Math.floor(Math.random() * taunts.length)]; // 랜덤 조롱 대사 표시
                setTimeout(() => {
                    showBalloon = false; // 말풍선 숨기기
                    balloon.style.display = 'none';
                }, 2000); // 2초 후에 말풍선 숨김
            }

            requestAnimationFrame(gameLoop); // 게임 루프 계속 실행
        }
    </script>
</body>
</html>
