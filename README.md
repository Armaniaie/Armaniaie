```
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

// Game variables
int score = 0;
int playerSpeed = 50;
int nitro = 0;
int brakes = 0;
int tyres = 0;
int alloys = 0;
int headlights = 0;
int colour = 0;

// Garage variables
int garageCars[10] = {0};
int currentCar = 0;

// Mission variables
int missions[10] = {0};
int missionCompleted = 0;

// Settings variables
int graphics = 60;
int sound = 1;
int music = 1;

// Function to draw the game
void drawGame() {
	printf("Score: %d\n", score);
	printf("Player Speed: %d\n", playerSpeed);
	printf("Nitro: %d\n", nitro);
	printf("Brakes: %d\n", brakes);
	printf("Tyres: %d\n", tyres);
	printf("Alloys: %d\n", alloys);
	printf("Headlights: %d\n", headlights);
	printf("Colour: %d\n", colour);
}

// Function to draw the garage
void drawGarage() {
	printf("Garage:\n");
	for (int i = 0; i < 10; i++) {
		printf("Car %d: %d\n", i, garageCars[i]);
	}
	printf("Current Car: %d\n", currentCar);
}

// Function to draw the missions
void drawMissions() {
	printf("Missions:\n");
	for (int i = 0; i < 10; i++) {
		printf("Mission %d: %d\n", i, missions[i]);
	}
	printf("Mission Completed: %d\n", missionCompleted);
}

// Function to draw the settings
void drawSettings() {
	printf("Settings:\n");
	printf("Graphics: %d\n", graphics);
	printf("Sound: %d\n", sound);
	printf("Music: %d\n", music);
}

// Function to upgrade the car
void upgradeCar(int upgrade) {
	switch (upgrade) {
		case 1:
			playerSpeed += 10;
			break;
		case 2:
			nitro += 10;
			break;
		case 3:
			brakes += 10;
			break;
		case 4:
			tyres += 10;
			break;
		case 5:
			alloys += 10;
			break;
		case 6:
			headlights = !headlights;
			break;
		case 7:
			colour = rand() % 10;
			break;
	}
}

int main() {
	srand(time(NULL));
	while (1) {
		drawGame();
		drawGarage();
		drawMissions();
		drawSettings();
		printf("Enter 1 to upgrade car, 2 to complete mission, 3 to change settings: ");
		int input;
		scanf("%d", &input);
		switch (input) {
			case 1:
				upgradeCar(rand() % 7 + 1);
				break;
			case 2:
				missionCompleted = 1;
				upgradeCar(rand() % 7 + 1);
				break;
			case 3:
				printf("Enter 1 to change graphics, 2 to change sound, 3 to change music: ");
				int settingInput;
				scanf("%d", &settingInput);
				switch (settingInput) {
					case 1:
						graphics = rand() % 100 + 1;
						break;
					case 2:
						sound = rand() % 2;
						break;
					case 3:
						music = rand() % 2;
						break;
				}
				break;
		}
	}
	return 0;
}
```
