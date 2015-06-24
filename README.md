# Collections
It contains java program files to understand implementations of collections
----------------------------------------------------------------------------------------
package collectionsfiles;

import java.util.HashMap;
import java.util.HashSet;
import java.util.Iterator;
import java.util.Map;
import java.util.Scanner;
import java.util.Set;

public class CollectionImplementation {

	Set<String> name = new HashSet<String>();
	Map<String, Integer> m = new HashMap<String, Integer>();

	public static void main(String args[]) {

		CollectionImplementation student = new CollectionImplementation();
		CollectionImplementation lang = new CollectionImplementation();
		String str = "";
		boolean p;
		while (p = true) {
			Scanner sc = new Scanner(System.in);
			System.out.println("enter your access\n 1. Admin\n 2. Student");
			//String access = sc.next().toLowerCase();
			int access=sc.nextInt();;
			switch (access) {
			case 1: {
				boolean option = true;
				while (option == true) {
					System.out.println("Please choose \n 1.DeleteStuentName \n 2. DeleteRecord \n 3. Exit");
		
					int action = sc.nextInt();
					switch (action) {
					case 1: {
						System.out.println("Print student name to be deleted");
						String DeleteName = sc.next();
						if (student.name.contains(DeleteName.toLowerCase())) {
							student.name.remove(DeleteName);
							Iterator itr = student.name.iterator();
							while (itr.hasNext()) {
								System.out
										.println("student in the list are \n:"
												+ itr.next());
							}
						} else {
							System.out.println("name not present");
						}option= false;break;
					}
					case 2:{
						System.out.println("Please enter language to delete");
						String language= sc.next().toLowerCase();
						student.m.remove(language);
						Set spqr=student.m.entrySet();
						Iterator itr= spqr.iterator();
						System.out.println("Language in the list are \n:");
						while(itr.hasNext()){
							Map.Entry map = (Map.Entry) itr.next();
							System.out.println(map.getKey() + " : "
									+ map.getValue());
							
						} option=false;break;
					}
					case 3:{
						option= false;
						break;
					}
					}
				}
				//option = false;
				break;
			}
			case 2: {

				System.out.println("Kindly enter your name");

				String studentname = sc.next().toLowerCase();

				if ((student.name).contains(studentname)) {
					System.out.println("Already registered");
					p = false;
				} else {
					student.name.add(studentname);
					System.out.println("What is your favorite language");
					str = sc.next();
					if (student.m.containsKey(str)) {
						int count = student.m.get(str);
						count++;
						student.m.put(str, count);
					} else {
						student.m.put(str, 1);
					}
					Set s = student.m.entrySet();
					Iterator it = s.iterator();
					while (it.hasNext()) {
						Map.Entry map = (Map.Entry) it.next();
						System.out.println(map.getKey() + " : "
								+ map.getValue());
					}
					p = false;
				}
			}

			}
		}
	}
}
