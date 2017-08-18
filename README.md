# BigONotation
A group of algorithms to analyze performance

package com.Concept;

public class BigONotation {
	
	private int[] newArray;
	private int ArraySize;
	private int itemsInArray = 0;
	
	long startTime, endTime;
	
	public BigONotation(int size){
		
		ArraySize = size;
		newArray = new int[size];
	}
	
	public void bubbleSort(){
		
		startTime = System.currentTimeMillis();
		
		for(int A = 0; A < ArraySize; A++){
			for(int B = 0; B < A; B++){
				if(newArray[B] < newArray[B+1]){
					swapValues(B,B+1);
				}
			}
		}
		
		endTime = System.currentTimeMillis();
		System.out.println("Bubble sort time: " +(endTime - startTime));
	}
	public void binarySearchArray(int value){
		
		int lowIndex = 0;
		int highIndex = ArraySize - 1;
		
		int throughTime = 0;
		
		startTime = System.currentTimeMillis();
		while(lowIndex < highIndex){
			
			int middleIndex = (lowIndex + highIndex) / 2;
			if(newArray[middleIndex] > value ){
				
				lowIndex = middleIndex + 1;
			} else if(newArray[middleIndex] < value){
				
				highIndex = middleIndex - 1;
			} else{
				System.out.println("Found a match: "+middleIndex);
				highIndex = middleIndex + 1;
			}
		
			throughTime++;
		}
		
		endTime = System.currentTimeMillis();
		System.out.println("Through time: "+throughTime);
		System.out.println("Binary search time: "+ (endTime - startTime));
	
	}
	public void linearSearhArray(int value){
		
		boolean valueInArray = false;
		String indexInArray = " ";
		
		startTime = System.currentTimeMillis();
		
		for(int A = 0; A < ArraySize; A++){
			if(newArray[A] == value){
				
				valueInArray = true;
				indexInArray += A + " ";
			}
		}
		
		endTime = System.currentTimeMillis();
		System.out.println("Value in search: "+valueInArray );
		System.out.println("Linear search time: "+ (endTime - startTime));
		
	}
	
	public void generateArray(){
		
		for(int A = 0; A < ArraySize; A++){
			
			newArray[A] = (int) (Math.random()*1000) + 10;
		}
		
		itemsInArray = ArraySize - 1;
	}
	public void swapValues(int firstIndex, int secondIndex){
		
		int temp = newArray[firstIndex];
		newArray[firstIndex] = newArray[secondIndex];
		newArray[secondIndex] = temp;
		
	}

	public static void main(String[] args) {
		
		BigONotation ONotation = new BigONotation(900000);
		
		ONotation.linearSearhArray(400);
		ONotation.binarySearchArray(900);
		ONotation.bubbleSort();

	}

}
