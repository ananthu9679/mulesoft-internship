package net.java;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

public class cinema {

	public static void main(String[] args) {
		
		String url = "jdbc:sqlite:/D:\\sqlite\sqlite-tools-win32-x86-3360000\\cinemadb.db"; 
	try {			
        Connection connection = DriverManager.getConnection(url);
        String sql = "SELECT * FROM Movies";
        
        Statement statement = connection.createStatement();
        ResultSet result = statement.executeQuery(sql);
        
        while(result.next()) {
        	String moviename = result.getString("moviename");
        	String actor = result.getString("actor");
        	String actress = result.getString("actress");
        	String director = result.getString("director");
        	Integer year = result.getInt("year of release");
        	
        	System.out.println(moviename + "|" + actor + "|" + actress +"|" + director + "|" + year); 
        }
	}catch (SQLException e) {
		System.out.println("error");
		e.printStackTrace();
	}
		
	}

}
