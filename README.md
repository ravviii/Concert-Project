# Concert-Project
import java.util.*;

public class TeamProject {

	public static void main(String[] args) {
		
		// Declaring all variables at once for easy access
		
		// Number of Total Tickets
		int ticketNum = 0;
		
		// Declares whether user gets a bundle discount
		boolean hotelNeeded = false;
		boolean lockerNeeded = false;
		
		//Ticket Prices
		double ticketPriceGA = 100;
		double ticketPriceGAPlus = 150;
		double ticketPriceVIP = 200;
		
		// Determines User Ticket Type
		double ticketOption = 0;
		
		//Locker Prices
		double lockerPrice1 = 40;
		double lockerPrice2 = 60;
		double lockerPrice3 = 80;
		
		//Determines User Locker Type
		double lockerOption = 0;
		
		//Hotel Prices
		double hotelPrice1 = 200;
		double hotelPrice2 = 350;
		double hotelPrice3 = 500;
		
		//Determines User Hotel Type
		double hotelOption = 0;
		
		//Determines Number of Days
		double numTicketDays = 0;
		double numHotelDays = 0;
		double numLockerDays = 0;
		
		//Takes User Input if Hotel and Locker are needed
		int numHotel = 0;
		int numLocker = 0;
		
		//Discount Rates
		double ticketDiscountRate = 0;
		double packageDiscount = 0;
		
		//Total Prices 
		double totalPackagePrice = 0;
		double totalTicketPrice = 0;
		double totalHotelPrice = 0;
		double totalLockerPrice = 0;
		double totalCartAmount = 0;
		
		//Determines if another ticket is needed
		int nextTicket = 0;
		
		
		// Declaring Arrays
		double[] ticket1 = new double[10];
		
		double[] ticket2 = new double[10];
		
		double[] ticket3 = new double[10];
		
		//Main Do-While Loop for Individual Tickets
		do {
			
		//Refreshes Values that will be used for every ticket
		numTicketDays = 0;
		ticketOption = 0;
		totalTicketPrice = 0;
		hotelOption = 0;
		numHotelDays = 0;
		totalHotelPrice = 0;		
		lockerOption = 0;
		numLockerDays = 0;
		totalLockerPrice = 0;
		totalPackagePrice = 0;
		hotelNeeded = false;
		lockerNeeded = false;
		
		//Adds a count for every ticket processed	
		ticketNum++; 
		
		Scanner reader = new Scanner(System.in);
		
		//Tickets Section
		System.out.print("How many days for this ticket? (3 max): ");
		numTicketDays = reader.nextDouble();
	
		System.out.println("\nSelect a Ticket Option");
		System.out.println("------------------------");

		System.out.printf("1 for GA: $%.2f",ticketPriceGA);
		System.out.printf("\n2 for GA+: $%.2f",ticketPriceGAPlus);
		System.out.printf("\n3 for VIP: $%.2f",ticketPriceVIP);
		System.out.println();
		System.out.print("\nWhich ticket would you like to buy?: ");
		ticketOption = reader.nextDouble();
		
		//Displays Cart Amount
		totalTicketPrice = TotalTicketPriceMethod(ticketOption,numTicketDays);
		totalPackagePrice += totalTicketPrice;
		totalCartAmount += totalTicketPrice;
		
		System.out.println("\nAdded to cart");
		System.out.println("=============================");
		System.out.printf("Personal Cart: $%.2f ",totalPackagePrice); //Method being called
		System.out.printf("\nTotal Cart: $%.2f ",totalCartAmount); //Method being called
		System.out.println("\n=============================");

		//Hotel Section
		System.out.print("\nIs a hotel needed? (1) for Yes (2) for No: ");
		numHotel = reader.nextInt();
		
		if (numHotel == 1) { // If they select Yes
			
			hotelNeeded = true; // Determines whether or not discount is applied at the end
			
			System.out.println("\nSelect a Hotel Option: ");
			System.out.println("-------------------------");
			System.out.println("Hotel 1: $" + hotelPrice1 + " per night.");
			System.out.println("Hotel 2: $" + hotelPrice2 + " per night.");
			System.out.println("Hotel 3: $" + hotelPrice3 + " per night.");
			System.out.print("\nWhich hotel would you like to buy?: ");
			hotelOption = reader.nextDouble();
		
			System.out.print("\n*Same amount of days as tickets? (1) for Yes (2) for No: ");
			
			int sameNight = reader.nextInt(); // Temp Variable used for if-else
			
			if(sameNight == 1) {
				numHotelDays = numTicketDays;
			}
			
			else {
				System.out.print("\nHow many days? (3 max): ");
				numHotelDays = reader.nextDouble();
			}
			
			//Displays Cart Amount
			totalHotelPrice = TotalHotelPriceMethod(hotelOption,numHotelDays);
			totalPackagePrice += totalHotelPrice; 
			totalCartAmount += totalHotelPrice;
			System.out.printf("\nYour total hotel price comes out to: $%.2f for %.0f day(s).",totalHotelPrice,numHotelDays); 
			System.out.println("\nAdded to cart");
			System.out.println("=============================");
			System.out.printf("Personal Cart: $%.2f ",totalPackagePrice); //Method being called
			System.out.printf("\nTotal Cart: $%.2f",totalCartAmount);
			System.out.println("\n=============================");
		}
		
		//Lockers Section
		System.out.print("\nIs a locker needed? (1) for Yes (2) for No: ");
		numLocker = reader.nextInt();

		if (numLocker == 1) {
			
			lockerNeeded = true; //Determines whether or not discount is applied at the end
			
			System.out.println("\nSelect a Locker Option: ");
			System.out.println("--------------------------");
			System.out.println("Locker 1: $" + lockerPrice1 + " per night.");
			System.out.println("Locker 2: $" + lockerPrice2 + " per night.");
			System.out.println("Locker 3: $" + lockerPrice3 + " per night.");
			System.out.print("\nWhich locker would you like to buy?: ");
			lockerOption = reader.nextInt();
			
		
			System.out.print("\n*Same amount of days as tickets? (1) for Yes (2) for No: ");
			
			int sameNight = reader.nextInt(); //Temp. variable used for if-else
			
			if(sameNight == 1) {
				numLockerDays = numTicketDays;
			}
			
			else {
				System.out.print("\nHow many days?: ");
				numLockerDays = reader.nextDouble();
			}
			
			//Displays Cart Amount
			totalLockerPrice = TotalLockerPriceMethod(lockerOption,numLockerDays);
			totalPackagePrice += totalLockerPrice; 
			totalCartAmount += totalLockerPrice;
			
			System.out.printf("\nYour total locker price comes out to: $%.2f for %.0f day(s).",totalLockerPrice,numLockerDays); //Method being called
			System.out.println("\nAdded to cart");
		}
		
		
		
		///Adds discount to individual customer's package.
		//If both conditions are met, apply discount
		if (hotelNeeded && lockerNeeded) { 
				packageDiscount = 0.15 * totalPackagePrice;
				totalPackagePrice -= packageDiscount;
				totalCartAmount -= packageDiscount; 
				System.out.println("\n---------------------------");
				System.out.println("15% Package Discount Applied");
				System.out.println("---------------------------");
		}
		
		

		//Displays Items In Cart
		System.out.println("\n============================================");
		System.out.printf("Your ticket for %.0f day(s) totals to $%.2f",numTicketDays,TotalTicketPriceMethod(ticketOption,numTicketDays));
		System.out.printf("\nYour hotel for %.0f day(s) totals to $%.2f.",numHotelDays,TotalHotelPriceMethod(hotelOption,numHotelDays));
		System.out.printf("\nYour locker for %.0f day(s) totals to $%.2f.",numLockerDays,TotalLockerPriceMethod(lockerOption,numLockerDays));
		System.out.println("\n============================================");
		System.out.printf("\nPersonal Cart Price: $%.2f",totalPackagePrice);
		System.out.printf("\nTotal Cart Price: $%.2f",totalCartAmount);
		System.out.println("\n============================================");
		
		

		//Array Implementation through switch statement:
		//Adds respective values to individual indexes 
		switch (ticketNum) {
		case 1: ticket1[0] = numTicketDays;
				ticket1[1] = ticketOption;
				ticket1[2] = totalTicketPrice;
				ticket1[3] = hotelOption;
				ticket1[4] = numHotelDays;
				ticket1[5] = totalHotelPrice;		
				ticket1[6] = lockerOption;
				ticket1[7] = numLockerDays;
				ticket1[8] = totalLockerPrice;
				ticket1[9] = totalPackagePrice;
				break;
				
		case 2: ticket2[0] = numTicketDays;
				ticket2[1] = ticketOption;
				ticket2[2] = totalTicketPrice;
				ticket2[3] = hotelOption;
				ticket2[4] = numHotelDays;
				ticket2[5] = totalHotelPrice;		
				ticket2[6] = lockerOption;
				ticket2[7] = numLockerDays;
				ticket2[8] = totalLockerPrice;
				ticket2[9] = totalPackagePrice;
				break;
				
		case 3: ticket3[0] = numTicketDays;
				ticket3[1] = ticketOption;
				ticket3[2] = totalTicketPrice;
				ticket3[3] = hotelOption;
				ticket3[4] = numHotelDays;
				ticket3[5] = totalHotelPrice;		
				ticket3[6] = lockerOption;
				ticket3[7] = numLockerDays;
				ticket3[8] = totalLockerPrice;
				ticket3[9] = totalPackagePrice;
				break;
		}
		
		System.out.print("\n\nDo you need another ticket? (1) for Yes (2) for No: ");
		nextTicket = reader.nextInt();

		if (ticketNum == 3 && nextTicket == 1) {
			System.out.println("----------------------------");
			System.out.println("Sorry, you have exceeded your ticket limit.");
			System.out.println("----------------------------");
		}
		
		} while (nextTicket == 1 && ticketNum < 3);

		
		//Adds all individual ticket prices
		double totalConcertTicketPrice = ticket1[2]+ticket2[2]+ticket3[2];
		double totalConcertHotelPrice = ticket1[5]+ticket2[5]+ticket3[5];
		double totalConcertLockerPrice = ticket1[8]+ticket2[8]+ticket3[8];

		//Checkout
		System.out.println("\n=============================");
		System.out.printf("Total Ticket Count: %d",ticketNum);
		System.out.printf("\nTotal Ticket Price: $%.2f",totalConcertTicketPrice);
		System.out.printf("\nTotal Hotel Price: $%.2f",totalConcertHotelPrice);
		System.out.printf("\nTotal Locker Price: $%.2f", totalConcertLockerPrice);
		if (ticketNum == 3){
			System.out.println("\n----------------------------");
			System.out.println("You have more than 3 Tickets.");
			System.out.println("You Get a 10% Discount.");
			System.out.println("----------------------------");
			//Applies Discount to entire cart if there are 3 or more tickets
			ticketDiscountRate = .10 * totalCartAmount;
			totalCartAmount -= ticketDiscountRate; 

		}
		
		System.out.println("\n=======================================");
		System.out.printf("Your Total Price comes out to: $%.2f", totalCartAmount);
		System.out.println("\n=======================================");
		
		System.out.println("\nEnd of Program");
		
	}
	
	//Total Ticket Price Method
	public static double TotalTicketPriceMethod(double type, double days) {
		double totalPrice = 0;
		double ticketPriceGA = 100;
		double ticketPriceGAPlus = 150;
		double ticketPriceVIP = 200;
		
		if (type == 1) {
			totalPrice = ticketPriceGA * days; 
		}
		else if (type == 2) {
			totalPrice = ticketPriceGAPlus * days;
		}
		else if (type == 3) {
			totalPrice = ticketPriceVIP * days;
		}
		return totalPrice;
	}
	
	//Total Hotel Price Method
	public static double TotalHotelPriceMethod(double type, double days) {
		double totalPrice = 0;
		double hotelPrice1 = 200;
		double hotelPrice2 = 350;
		double hotelPrice3 = 500;
		
		if (type == 1) {
			totalPrice = hotelPrice1 * days; 
		}
		else if (type == 2) {
			totalPrice = hotelPrice2 * days;
		}
		else if (type == 3) {
			totalPrice = hotelPrice3 * days;
		}
		return totalPrice;
	}
	
	//Total Locker Price Method
	public static double TotalLockerPriceMethod(double type, double days) {
		double totalPrice = 0;
		double lockerPrice1 = 40;
		double lockerPrice2 = 60;
		double lockerPrice3 = 80;
		
		if (type == 1) {
			totalPrice = lockerPrice1 * days; 
		}
		else if (type == 2) {
			totalPrice = lockerPrice2 * days;
		}
		else if (type == 3) {
			totalPrice = lockerPrice3 * days;
		}
		return totalPrice;
	}
}
