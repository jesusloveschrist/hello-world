import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.OutputStreamWriter;
import java.net.URL;
import java.net.URLConnection;
import java.net.URLEncoder;
 
public class Sendsms {
	public static String Sendsms()
	{
		try {
			// Construct data
			String apiKey = "apikey=" + URLEncoder.encode("gZiUL9RvVro-M6HEmdMAfItmSm03aC0nrttxXm3XUR", "UTF-8");
			String message = "&message=" + URLEncoder.encode("Hai Sir", "UTF-8");
			String sender = "&sender=" + URLEncoder.encode("Sneha Thomas", "UTF-8");
			String numbers = "&numbers=" + URLEncoder.encode("9746776694", "UTF-8");
			
			System.out.println("apiKey ::"+apiKey);
			System.out.println("message ::"+message);
			System.out.println("sender ::"+sender);
			System.out.println("numbers ::"+numbers);
			
			// Send data
			String data = "https://api.txtlocal.com/send/?" + apiKey + numbers + message + sender;
			URL url = new URL(data);
			URLConnection conn = url.openConnection();
			conn.setDoOutput(true);
			
			// Get the response
			BufferedReader rd = new BufferedReader(new InputStreamReader(conn.getInputStream()));
			String line;
			String sResult="";
		    while ((line = rd.readLine()) != null) {
			// Process line...
				sResult=sResult+line+" ";
			}
			rd.close();
			
			return sResult;
		} catch (Exception e) {
			System.out.println("Error SMS "+e);
			return "Error "+e;
		}
	}
	public static void main(String args[]){
		String output= "";
		System.out.println("*******Calling SMS Method*******");
		output = Sendsms();
		System.out.println("*******DONE SMS Method*******");
		System.out.println("output is :: "+output);
		
		
		
	}

}

