# colormotor

static void rootfunc(void * arg) {
	motor_init();  //모터초기화
	encoder_init();  //모터초기화
	glcd_init();  //glcd초기화

	ev3_sensor_init(0, COL_COLOR);  //ev3센서 COLOR모드 초기화

	for(;;){
		switch(ev3_sensor_get(0))
		{
		case RED:  //센서값 빨간색이면
			motor_set(0,200);  //모터속도 200
			break;
		case GREEN:  //센서값 초록색이면
			motor_set(0,500);  //모터속도 500
			break;
		case BLUE:  //센서값 파란색이면
			motor_set(0,800);  //모터속도 800
			break;
		}
		task_sleep(50);  //50ms주기 측정
	}

}