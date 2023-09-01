#include <iostream>
#include <string>
#include <iomanip>
using namespace std;

const int ROWS = 9;
const int COLS = 9;
const int NUMOFQUADRANTS = 9;

bool scannedTopLeftQuad = false;
bool scannedTopCenterQuad = false;
bool scannedTopRightQuad = false;
bool scannedMidLeftQuad = false;
bool scannedMidCenterQuad = false;
bool scannedMidRightQuad = false;
bool scannedBottomLeftQuad = false;
bool scannedBottomCenterQuad = false;
bool scannedBottomRightQuad = false;

bool scannedTopLeftQuadForSingleDigit = false;
bool scannedTopCenterQuadForSingleDigit = false;
bool scannedTopRightQuadForSingleDigit = false;
bool scannedMidLeftQuadForSingleDigit = false;
bool scannedMidCenterQuadForSingleDigit = false;
bool scannedMidRightQuadForSingleDigit = false;
bool scannedBottomLeftQuadForSingleDigit = false;
bool scannedBottomCenterQuadForSingleDigit = false;
bool scannedBottomRightQuadForSingleDigit = false;

bool scannedTopCenterAndTopRightForSameDigit = false;
bool scannedTopLeftAndTopRightForSameDigit = false;
bool scannedTopLeftAndTopCenterForSameDigit = false;
bool scannedMidCenterAndMidRightForSameDigit = false;
bool scannedMidLeftAndMidRightForSameDigit = false;
bool scannedMidLeftAndMidCenterForSameDigit = false;
bool scannedBottomCenterAndBottomRightForSameDigit = false;
bool scannedBottomLeftAndBottomRightForSameDigit = false;
bool scannedBottomLeftAndBottomCenterForSameDigit = false;

bool scannedMidLeftAndBottomLeftForSameDigit = false;
bool scannedTopLeftAndBottomLeftForSameDigit = false;
bool scannedTopLeftAndMidLeftForSameDigit = false;
bool scannedMidCenterAndBotCenterForSameDigit = false;
bool scannedTopCenterAndBotCenterForSameDigit = false;
bool scannedTopCenterAndMidCenterForSameDigit = false;
bool scannedMidRightAndBottomRightForSameDigit = false;
bool scannedTopRightAndBottomRightForSameDigit = false;
bool scannedTopRightAndMidRightForSameDigit = false;

bool scannedTopQuads = false;
bool scannedMidQuads = false;
bool scannedBottomQuads = false;

bool scannedLeftQuads = false;
bool scannedCenterQuads = false;
bool scannedRightQuads = false;

bool scannedRow1 = false;
bool scannedRow2 = false;
bool scannedRow3 = false;
bool scannedRow4 = false;
bool scannedRow5 = false;
bool scannedRow6 = false;
bool scannedRow7 = false;
bool scannedRow8 = false;
bool scannedRow9 = false;

bool scannedCol1 = false;
bool scannedCol2 = false;
bool scannedCol3 = false;
bool scannedCol4 = false;
bool scannedCol5 = false;
bool scannedCol6 = false;
bool scannedCol7 = false;
bool scannedCol8 = false;
bool scannedCol9 = false;

bool scannedTopRow = false;
bool scannedMidRow = false;
bool scannedBotRow = false;
bool scannedLeftCol = false;
bool scannedCenterCol = false;
bool scannedRightCol = false;

int puzzleInt[ROWS][COLS] = {
	{5,3,4,0,7,0,9,1,2},
	{6,0,0,1,9,5,0,0,8},
	{0,9,8,0,0,0,0,6,0},
	{8,0,0,0,6,0,0,0,3},
	{4,0,0,8,0,3,0,0,1},
	{7,0,0,0,2,0,0,0,6},
	{0,6,0,0,0,0,2,8,4},
	{2,8,7,4,1,9,0,0,5},
	{3,4,5,0,8,0,0,7,9}
};

int crossHatc[ROWS][COLS] = {
	{1,1,1,1,1,1,1,1,1},
	{1,1,1,1,1,1,1,1,1},
	{1,1,1,1,1,1,1,1,1},
	{1,1,1,1,1,1,1,1,1},
	{1,1,1,1,1,1,1,1,1},
	{1,1,1,1,1,1,1,1,1},
	{1,1,1,1,1,1,1,1,1},
	{1,1,1,1,1,1,1,1,1},
	{1,1,1,1,1,1,1,1,1},
};

int crossHatchQuadrant[3][3] = {
	{1,1,1},
	{1,1,1},
	{1,1,1}
};

int QuadrantX[3][3] = {
	{0,0,0},
	{0,0,0},
	{0,0,0}
};

int QuadrantY[3][3] = {
	{0,0,0},
	{0,0,0},
	{0,0,0}
};

int QuadrantZ[3][3] = {
	{0,0,0},
	{0,0,0},
	{0,0,0}
};

int QuadrantTopLeft[3][3] = {
	{0,0,0},
	{0,0,0},
	{0,0,0}
};

int QuadrantTopCenter[3][3] = {
	{0,0,0},
	{0,0,0},
	{0,0,0}
};

int QuadrantTopRight[3][3] = {
	{0,0,0},
	{0,0,0},
	{0,0,0}
};

int QuadrantMidLeft[3][3] = {
	{0,0,0},
	{0,0,0},
	{0,0,0}
};

int QuadrantMidCenter[3][3] = {
	{0,0,0},
	{0,0,0},
	{0,0,0}
};

int QuadrantMidRight[3][3] = {
	{0,0,0},
	{0,0,0},
	{0,0,0}
};

int QuadrantBotLeft[3][3] = {
	{0,0,0},
	{0,0,0},
	{0,0,0}
};

int QuadrantBotCenter[3][3] = {
	{0, 0, 0},
	{ 0,0,0 },
	{ 0,0,0 }
};
int QuadrantBotRight[3][3] = {
	{0,0,0},
	{0,0,0},
	{0,0,0}
};

enum quadrantLocation
{
	TOPLEFTQUAD, TOPCENTERQUAD, TOPRIGHTQUAD,
	MIDLEFTQUAD, MIDCENTERQUAD, MIDRIGHTQUAD,
	BOTLEFTQUAD, BOTCETNERQUAD, BOTRIGHTQUAD
};

enum rowLocations {
	ROW1, ROW2, ROW3, ROW4, ROW5, ROW6, ROW7, ROW8, ROW9
};

enum colLocations {
	COL1, COL2, COL3, COL4, COL5, COL6, COL7, COL8, COL9
};

int numsUsedArr[9] = { 0,0,0,0,0,0,0,0,0 };
void displaySudokuPuzzle();
bool foundIntInQuadrant(int keyToSearch, int quadrantID);
bool foundIntInRow(int keyToSearch, int rowIndex);
bool foundIntInCol(int keyToSearch, int colIndex);
bool isPuzzleComplete();
int rowIndexOfKeyInQuadrant(int key, int quadrantID);
int colIndexOfKeyInQuadrant(int key, int quadrantID);
bool isASingleZeroInThisQuadrant(int quadrantID);
bool isASingleZeroInThisRow(int rowIndex);
bool isASingleZeroInThisCol(int rowIndex);
int colIndexOfKeyInThisRow(int key, int rowIndex);
int rowIndexOfKeyInThisCol(int key, int colIndex);
void createCrossHatchedQuadrant(int key, int quadrantToBeCrossHatchedID);
bool doesCrossHatchedQuadrantHaveOnlyOneSquareAvailable();
void fillInSingleRemainingSquareInQuadrant(int key, int quadrantToFillID);
void fillInSingleSquareInRow(int rowIndex);
void fillInSingleSquareInCol(int colIndex);
void fillInQuadrants();
void updatePuzzleInts();
int whatSingleNumIsMissingInThisRow(int rowIndex);
int whatSingleNumIsMissingInThisCol(int colIndex);
int findAvailableColInCrossHatchedQuadrant();
int findAvailableRowInCrossHatchedQuadrant();
void setScannedFlagsToFalse();

int main() {
	//declarations
	int rowQuadrant = 0;
	int colQuadrant = 0;
	int numBeingInvestigated = 1;
	int numOfEmptySquares = 0;
	int numNotBeingUsed = 0;
	bool puzzleSolved = false;
	bool isOneSquareLeft = false;

	//display sudoku puzzle
	cout << "Original Sudoku Puzzle" << endl;
	cout << "**********************" << endl;
	displaySudokuPuzzle();

	//solve sudoku puzzle
	rowQuadrant = 1;
	colQuadrant = 1;
	fillInQuadrants();

	while (puzzleSolved == false)
	{
		int intCnt = 1;
		int cntCycles = 0;
		bool haveCycledThroughAllRowsAndCols = false;

		while (intCnt < 10) {
			if (intCnt == 10)
				cout << " ";
			else if (intCnt == 2)
				cout << " ";
			else if (intCnt == 3)
				cout << " ";
			else if (intCnt == 4)
				cout << " ";
			else if (intCnt == 5)
				cout << " ";
			else if (intCnt == 6)
				cout << " ";
			else if (intCnt == 7)
				cout << " ";
			else if (intCnt == 8)
				cout << " ";
			else if (intCnt == 9)
				cout << " ";

			//scan rows
			if (scannedRow1 == false) {
				scannedRow1 = true;
				if (isASingleZeroInThisRow(ROW1) == true) {
					fillInSingleSquareInRow(ROW1);
				}
				if (isASingleZeroInThisRow(ROW2) == true) {
					fillInSingleSquareInRow(ROW2);
				}
				if (isASingleZeroInThisRow(ROW3) == true) {
					fillInSingleSquareInRow(ROW3);
				}
				if (isASingleZeroInThisRow(ROW4) == true) {
					fillInSingleSquareInRow(ROW4);
				}
				if (isASingleZeroInThisRow(ROW5) == true) {
					fillInSingleSquareInRow(ROW5);
				}
				if (isASingleZeroInThisRow(ROW6) == true) {
					fillInSingleSquareInRow(ROW6);
				}
				if (isASingleZeroInThisRow(ROW7) == true) {
					fillInSingleSquareInRow(ROW7);
				}
				if (isASingleZeroInThisRow(ROW8) == true) {
					fillInSingleSquareInRow(ROW8);
				}
				if (isASingleZeroInThisRow(ROW9) == true) {
					fillInSingleSquareInRow(ROW9);
				}
			}

			else if (scannedCol1 == false) {
				scannedCol1 = true;
				if (IsASingleZeroInThisCol(COL1) == true) {
					fillInSingleSquareInCol(COL1);
				}
			}
				else if (scannedCol1 == false) {
				scannedCol1 = true;
				if (IsASingleZeroInThisCol(COL1) == true) {
					fillInSingleSquareInCol(COL1);
				}
			}
						else if (scannedCol2 == false) {
							scannedCol2 = true;
							if (IsASingleZeroInThisCol(COL2) == true) {
								fillInSingleSquareInCol(COL2);
							}
						}
							else if (scannedCol3 == false) {
								scannedCol3 = true;
								if (IsASingleZeroInThisCol(COL3) == true) {
									fillInSingleSquareInCol(COL3);
								}
							}
								else if (scannedCol4 == false) {
									scannedCol4 = true;
									if (IsASingleZeroInThisCol(COL4) == true) {
										fillInSingleSquareInCol(COL4);
									}
								}
									else if (scannedCol5 == false) {
										scannedCol5 = true;
										if (IsASingleZeroInThisCol(COL5) == true) {
											fillInSingleSquareInCol(COL5);
										}
									}
										else if (scannedCol6 == false) {
											scannedCol6 = true;
											if (IsASingleZeroInThisCol(COL6) == true) {
												fillInSingleSquareInCol(COL6);
											}
										}
											else if (scannedCol7 == false) {
												scannedCol7 = true;
												if (IsASingleZeroInThisCol(COL7) == true) {
													fillInSingleSquareInCol(COL7);
												}
											}
												else if (scannedCol8 == false) {
													scannedCol8 = true;
													if (IsASingleZeroInThisCol(COL8) == true) {
														fillInSingleSquareInCol(COL8);
													}
												}
													else if (scannedCol9 == false) {
														scannedCol9 = true;
														if (IsASingleZeroInThisCol(COL9) == true) {
															fillInSingleSquareInCol(COL9);
														}
													}


		}
	}
}

//now scan quads
else if (scannedTopLeftQuadForSingleDigit == false) {
scannedTopLeftQuadForSingleDigit = true;
if (isASingleZeroInThisQuadrant(TOPLEFTQUAD) = true) {
	fillInSingleRemainingSquareInQuadrant(TOPLEFTQUAD);
}

else if (scannedTopCenterQuadForSingleDigit == false) {
	scannedTopCenterQuadForSingleDigit = true;
	if (isASingleZeroInThisQuadrant(TOPCENTERQUAD) = true) {
		fillInSingleRemainingSquareInQuadrant(TOPCENTERQUAD);

	}

	else if (scannedTopRightQuadForSingleDigit == false) {
		scannedTopRightQuadForSingleDigit = true;
		if (isASingleZeroInThisQuadrant(TOPRIGHTQUAD) = true) {
			fillInSingleRemainingSquareInQuadrant(TOPRIGHTQUAD);

		}

		else if (scannedMidLeftQuadForSingleDigit == false) {
			scannedMidLeftQuadForSingleDigit = true;
			if (isASingleZeroInThisQuadrant(MIDLEFTQUAD) = true) {
				fillInSingleRemainingSquareInQuadrant(MIDLEFTQUAD);

			}

			else if (scannedMidCenterQuadForSingleDigit == false) {
				scannedMidCenterQuadForSingleDigit = true;
				if (isASingleZeroInThisQuadrant(MIDCENTERQUAD) = true) {
					fillInSingleRemainingSquareInQuadrant(MIDCENTERQUAD);

				}

				else if (scannedMidRightQuadForSingleDigit == false) {
					scannedMidRightQuadForSingleDigit = true;
					if (isASingleZeroInThisQuadrant(MIDRIGHTQUAD) = true) {
						fillInSingleRemainingSquareInQuadrant(MIDRIGHTQUAD);

					}

					else if (scannedBottomLeftQuadForSingleDigit == false) {
						scannedBottomLeftQuadForSingleDigit = true;
						if (isASingleZeroInThisQuadrant(BOTTOMLEFTQUAD) = true) {
							fillInSingleRemainingSquareInQuadrant(BOTTOMLEFTQUAD);

						}

						else if (scannedBottomCenterQuadForSingleDigit == false) {
							scannedBottomCenterQuadForSingleDigit = true;
							if (isASingleZeroInThisQuadrant(BOTTOMCENTERQUAD) = true) {
								fillInSingleRemainingSquareInQuadrant(BOTTOMCENTERQUAD);

							}

							else if (scannedBottomRightQuadForSingleDigit == false) {
								scannedBottomRightQuadForSingleDigit = true;
								if (isASingleZeroInThisQuadrant(BOTTOMRIGHTQUAD) = true) {
									fillInSingleRemainingSquareInQuadrant(BOTTOMRIGHTQUAD);
								}

							}
						}
					}
				}
			}
		}
	}
}
		

void displaySudokuPuzzle() {
	for (int i = 0; i < ROWS; i++)
	{
		for (int j = 0; j < COLS; j += 3) //Draw a row of the puzzle
		{
			cout << "|";
				if (puzzleInt[i][j] == 0)
				cout << " ";
			else
				cout << puzzleInt[i][j] << " ";

			if (puzzleInt[i][j + 1] == 0)
				cout << " ";
			else
				cout << puzzleInt[i][j + 1] << " ";

			if (puzzleInt[i][j + 2] == 0)
				cout << " ";
			else
				cout << puzzleInt[i][j + 2];
		}
		cout << "|" << endl;
		if (i == 2 || i == 5 || i == 8) {
			cout << "**************" << endl;
		}
	}

}

bool foundIntInQuadrant(int keyToSearch, int quadrantID) {
	for i = 0; i < 3; i++)
	{
		for (int j = 0; j < 3; j++)
		{
			if (quadrantID == TOPLEFTQUAD) {
				if (quadrantTopLeft[i][j] == keyToSearch)
					return true;
			}
			if (quadrantID == TOPCENTERQUAD) {
				if (quadrantTopCenter[i][j] == keyToSearch)
					return true;
			}
			if (quadrantID == TOPRIGHTQUAD) {
				if (quadrantTopRight[i][j] == keyToSearch)
					return true;
			}
			if (quadrantID == MIDLEFTQUAD) {
				if (quadrantMidLeft[i][j] == keyToSearch)
					return true;
			}
			if (quadrantID == MIDCENTERQUAD) {
				if (quadrantMidCenter[i][j] == keyToSearch)
					return true;
			}
			if (quadrantID == TOPLEFTQUAD) {
				if (quadrantTopLeft[i][j] == keyToSearch)
					return true;
			}
			if (quadrantID == TOPLEFTQUAD) {
				if (quadrantTopLeft[i][j] == keyToSearch)
					return true;
			}
			if (quadrantID == TOPLEFTQUAD) {
				if (quadrantTopLeft[i][j] == keyToSearch)
					return true;
			}
			if (quadrantID == TOPLEFTQUAD) {
				if (quadrantTopLeft[i][j] == keyToSearch)
					return true;
			}
		}
}
}
