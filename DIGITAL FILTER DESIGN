module fir_filter(
    input clk,
    input reset,
    input signed [15:0] x, // Input signal
    output signed [31:0] y // Output signal
);

    reg signed [15:0] b0, b1, b2, b3; // Filter coefficients
    reg signed [15:0] delay_line [3:0]; // Delay line for input samples
    reg signed [31:0] result;

    // Initialize filter coefficients
    always @(posedge clk or posedge reset) begin
        if (reset) begin
            b0 <= 16'h1000;                   
            b1 <= 16'h2000; // Coefficient 2.0
            b2 <= 16'h3000;                   
            b3 <= 16'h4000; // Coefficient 4.0
        end
    end

    // Shift input samples through delay line
    always @(posedge clk or posedge reset) begin
        if (reset) begin
            delay_line[0] <= 0;
            delay_line[1] <= 0;
            delay_line[2] <= 0;
            delay_line[3] <= 0;
        end else begin
            delay_line[0] <= x;
            delay_line[1] <= delay_line[0];
            delay_line[2] <= delay_line[1];
            delay_line[3] <= delay_line[2];
        end
    end

    // Calculate FIR filter output
    always @(posedge clk) begin
        result <= (b0 * delay_line[0]) + (b1 * delay_line[1]) + (b2 * delay_line[2]) + (b3 * delay_line[3]);
    end

    assign y = result;

endmodule


module fir_filter_tb;

    reg clk;
    reg reset;
    reg signed [15:0] x;
    wire signed [31:0] y;

    fir_filter uut (
        .clk(clk),
        .reset(reset),
        .x(x),
        .y(y)
    );

    initial begin
        clk = 0;
        forever #5 clk = ~clk;
    end

    initial begin
        reset = 1;
        #10 reset = 0;

        // Input signal
        x = 16'h1000;
        #10 x = 16'h2000;
        #10 x = 16'h3000;
        #10 x = 16'h4000;
        #10 x = 16'h5000;

        // Run simulation for 100 cycles
        #100;

        $finish;
    end

    initial begin
        $dumpfile("fir_filter.vcd");
        $dumpvars(0, fir_filter_tb);
    end

endmodule
