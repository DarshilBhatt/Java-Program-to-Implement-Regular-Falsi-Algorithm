public class RegularFalsi

{
    
    
    
    public double f(double x)
    
    {
        
        
 
         return Math.cos(x) - x * x * x;
 
       
    }
  
    public double findRoot(double s, double t, double e, int m)
    
    {
        
        double r = 0.0,fr;
        
        int n, side = 0;
 
        /** starting values at endpoints of interval **/
        
        double fs = f(s);
        
        double ft = f(t);
 
        for (n = 0; n < m; n++)
        
        {
 
            r = (fs * t - ft * s) / (fs - ft);
           
            if (Math.abs(t - s) < e * Math.abs(t + s)) 
                
                break;
            
            fr = f(r);
 
            if (fr * ft > 0)
            
            {
                
                /** fr and ft have same sign, copy r to t **/
                
                t = r; 
                
                ft = fr;
                
                if (side == -1) 
                    
                    fs /= 2;
                
                side = -1;
            
            }
            
            else if (fs * fr > 0)
            
            {
                
                /** fr and fs have same sign, copy r to s **/
                
                s = r;  
                
                fs = fr;
                
                if (side == +1) 
                
                ft /= 2;
                
                side = +1;
            
            }
            
            else
            
            {
                
                /** fr * f_ very small (looks like zero) **/
                
                break;
            
            } 
        
        }
        
        return r;
    
    }
    
    /** Main function **/
    
    public static void main(String[] args)
    
    {
        
        System.out.println("Regular Falsi Test ");
 
 
        RegularFalsi rf = new RegularFalsi();
        
        /** lower limit **/
        
        double s = 0;
        
        /** upper limit **/
        
        double t = 1;
        
        /** half of upper bound for relative error **/
        
        double e = 5E-15;
        
        /** number of iterations **/
        
        int iterations = 100;
 
 
        System.out.println("\nRoot : "+ rf.findRoot(s, t, e, iterations));
    
    }

}
